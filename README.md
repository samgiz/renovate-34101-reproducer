## Expected behaviour

Running renovate on this repository updates the version to 1.0.0+2, because that's Renovate's pep440 sorting places 1.0.0+2 higher than 1.0.0+1.

## Actual behaviour

I see the following debug output when I run renovate in a dry run:

```json
 "config": {
   "pip_requirements": [
     {
       "deps": [
         {
           "depName": "dummy",
           "packageName": "dummy",
           "currentValue": "==1.0.0+1",
           "datasource": "pypi",
           "currentVersion": "1.0.0+2",
           "updates": [],
           "versioning": "pep440",
           "warnings": [],
           "fixedVersion": "1.0.0+1"
         }
       ],
       "packageFile": "requirements.txt"
     }
   ]
 }
```

Note how `currentVersion` is incorrect, and therefore the updates array is empty. More details on why the bug happens can be found [here](https://github.com/renovatebot/renovate/discussions/34101#discussion-7928657)
