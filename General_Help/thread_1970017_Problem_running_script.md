---
title: "Problem running script"
date: 2012-04-30
forum: General Help
---

### Post by Pharoz on 2012-04-30
Hi guys, I'm having an issue running this script. 

If I run it with the "./script" command without the "#!/bin/sh" in the code, it works. 

However, when I put the "#!/bin/sh" in there, it bombs out with the following error: ./script: 18: 31: not found

Here's the script. Nothing fancy. 
```

#!/bin/sh
TMP_FILE="/tmp/last_num_of_files.tmp"
NUM_BEFORE=`cat ${TMP_FILE}`
NUM_NOW=`ls -1 /var/log/hosts | wc -l | awk '{print $1}'`
LATEST_FILE=`ls -1 /var/log/hosts | tail -n 1`
SENDER="test@test.com"
RECIPIENT="test@test.com"


if (( ${NUM_NOW} != ${NUM_BEFORE} )); then
     echo -e "Logfile: /var/log/hosts/$LATEST_FILE" | mail -s "New SysLog Host Detected: $LATEST_FILE" -r $SENDER $RECIPIENT
fi

exit 0
```

Any clues? I made sure that the file has the execute bit set.

---

### Post by newbie-user on 2012-04-30
You might be using bash.  Try
```
#!/bin/bash
```

---

### Post by Pharoz on 2012-04-30
> **newbie-user said:**
> You might be using bash.  Try
```
#!/bin/bash
```

Great!! Thanks, that worked!

---

