---
title: "Updating modification times with rsync etc?"
date: 2011-07-17
forum: General Help
---

### Post by anlag on 2011-07-17
So, I logged on briefly during my vacation to start a transfer of some 12 TB of data between machines using scp compiled for high performance networks. Unfortunately I omitted the flag to preserve modification times. It's not critical but I'm wondering if there's a nice way to get them back. 

My first thought was to simply rsync the files from source to target with the archive flag set; since they already exist on the target, rsync should only need minimal effort to check that it's all there and then simply update the mod time. However, doing this takes nearly as long as the initial file transfer did, perhaps because the individual files are rather large (some 80 GB each.)

Encryption is not necessary for the transfer, so I was looking to turn that off. So far the only way I've found to do that is by using an rsync daemon on the target machine and then rsync over using that method. It might be an option but if possible I'd rather avoid messing about with that particular machine.

My main question is: can I "fix" the time stamps on the target 
machine without either using rsync-daemon, or transferring the files all over again? 

Cheers.

---

### Post by mikejonesey on 2011-07-17
rsync -c will sync files on a checksum so it does not compare files on mod time or size... or --size-only will as you may guess sync only based on file size... (risky for code, but with files with large GB like yours should be ok)...

---

### Post by mikejonesey on 2011-07-17
ps i could write you a quick bash script to syn the file times only if you like?

---

### Post by mikejonesey on 2011-07-17
save the following as date-sync.sh in the dir you wish to attain the dates from; run it, then copy the output.sh file to the destination machine sync dir and run output.sh, it will modify the mod dates of all the files...

```
#!/bin/bash
find . -maxdepth 1 -type f | while read filename; do
    if [ "$filename" != "date-sync.sh" -a "$filename" != "output.sh" ]; then
        echo "Syncing $filename"
        modTime=$(ls -la --full-time $filename | cut -d " " -f 6-7 | cut -b 1-19)
        echo "touch -d \"$modTime\" $filename" >> output.sh
    else
        echo "Skipping $filename"
    fi
done
```

---

### Post by anlag on 2011-07-17
Thanks a lot! I appreciate that greatly, your script worked perfectly and conveniently. I made a small modification; since I didn't transfer the entire directory the files were in (no way you could know that of course) the script would have created an empty file for each file that wasn't transferred over, so I simply added a test for the existence of the file in the execution lines sent to output.sh. Posting it in case anyone else wants to use it for similar purposes.

```
#!/bin/bash
find . -maxdepth 1 -type f | while read filename; do
    if [ "$filename" != "date-sync.sh" -a "$filename" != "output.sh" ]; then
        echo "Syncing $filename"
        modTime=$(ls -la --full-time $filename | cut -d " " -f 6-7 | cut -b 1-19)
        echo "if [ -e $filename ] ; then touch -d \"$modTime\" $filename ; fi" >> output.sh
    else
        echo "Skipping $filename"
    fi
done
```

Again, thank you. =D>

---

### Post by mikejonesey on 2011-07-17
no prob, one last tweek :)

```
#!/bin/bash

echo "#!/bin/bash" > output.sh
echo "function touchMe() { if [ -f \"\$2\" ]; then touch -d \"\$1\" \"\$2\"; echo \"updated mod date of \$2\"; fi }" >> output.sh

find . -maxdepth 1 -type f | while read filename; do
    if [ "$filename" != "./date-sync.sh" -a "$filename" != "./output.sh" ]; then
        echo "Syncing $filename"
        modTime=$(ls -la --full-time $filename | cut -d " " -f 6-7 | cut -b 1-19)
        echo "touchMe \"$modTime\" \"$filename\"" >> output.sh
    fi
done
```

---

