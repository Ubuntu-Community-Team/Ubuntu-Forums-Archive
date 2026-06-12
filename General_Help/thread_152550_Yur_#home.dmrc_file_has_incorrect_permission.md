---
title: "Yur #home/.dmrc file has incorrect permission"
date: 2006-03-30
forum: General Help
---

### Post by mitjab on 2006-03-30
Yur #home/.dmrc file has incorrect permission and it is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permission.

I did exactly this
```
chmod 644 /home/mitjab/.dmrc
```

but still this message appears after each new login

---

### Post by codejunkie on 2006-03-30
[QUOTE=mitjab]Yur #home/.dmrc file has incorrect permission and it is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permission.

I did exactly this
```
chmod 644 /home/mitjab/.dmrc
```

but still this message appears after each new login[/QUOTE]
run the command as root ```
sudo chmod 644 /home/mitjab/.dmrc
```also run ```
sudo chown mitjab:mitjab /home/mitjab/.dmrc
``` to change the ownership of the file to your user.

---

### Post by mitjab on 2006-03-30
thx for so quick replay but not working, i still get that message

---

### Post by codejunkie on 2006-03-30
[QUOTE=mitjab]thx for so quick replay but not working, i still get that message[/QUOTE]
try renaming the file with
```
sudo mv /home/mitjab/.dmrc /home/mitjab/old.dmrc
```
reboot and it will create a new one, that should fix it.

---

### Post by mitjab on 2006-03-30
still the same

---

### Post by codejunkie on 2006-03-30
[QUOTE=mitjab]still the same, now i even can't restart computer when i click on logout i only can logout and nothing else.[/QUOTE]
im lost on this one then, that should have taken care of it, if the permissions got changed.

---

### Post by trent dillman on 2006-03-30
The permissions should be 600, not 644.

jeff@ubuntu:~$ ls -l ~/.dmrc
-rw------- 1 jeff jeff 26 2006-03-07 04:39 /home/jeff/.dmrc

---

### Post by mitjab on 2006-03-30
now i don't get this message any more and i did that

```
chmod 755 -R ~/
sudo chown -R mitjab:mitjab /home/mitjab
sudo chmod 644 /home/mitjab/.dmrc
sudo chown mitjab:mitjab /home/mitjab/.dmrc
```

Thx all for help

---

### Post by wilberfan on 2006-10-21
Whew...!   I had this same problem...   This thread allowed me to fix it!

Thanks!

---

### Post by GratefulDiver on 2006-12-08
Just another note for some folks that might stumble onto this..

I gave myself this problem a few months back and hadn't caught it right away because I simply hadn't rebooted or even logged out in that whole time.  (Yeah, try THAT with a M$ OS!)

Anyway... - I was tweaking VSFTPD around and apparently in the process thought it might be a good idea to change my home dir to / so that if I ftp into it (which I did, many times) I wouldn't get caged into my home dir like the rest of the shlums.

After stewing a bit, I remembered and changed my home back to /home/<mylogin> and life seemed a little bit brighter.

Good luck! - And more important, PAY ATTENTION!  ;)

---

### Post by JamieEdwardClarke on 2008-07-04
Thanks, I tried exactly the code that mitjab gave at the end there and it fixed my 'puter too!

---

