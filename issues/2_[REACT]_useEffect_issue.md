

## Issue: 
A state only get the newest in useEffect. If call a function in ANOTHER useEffect of this state. The state we get not the newest.

## Demo:
```
WHEN myState2 BE CHANGED IN STORE
the components will have this behaviour

const myState1 = useAppSelector(state => state[ns]?.myState1 || null)
const myState2 = useAppSelector(state => state[ns]?.myState2 || null)

// here will show the newest state of myState2
console.log('COMP', myState2)

// a simple test function
const isShowWarningLeavePage = () => {
    // here will NOT show the newest state of myState2
    // it show the last myState2 when it call
    // because its call inside useEffect
    console.log('isShowWarningLeavePage: ',myState2)
}

useEffect(() => {
    // here will show the newest state of myState2
    console.log('useEffect myState2: ',myState2)
}, [myState2])

useEffect(() => {
    // here will NOT show the newest state of myState2
    console.log('useEffect isWarned: ',myState2)
    isShowWarningLeavePage()
}, [isWarned])

}
```

