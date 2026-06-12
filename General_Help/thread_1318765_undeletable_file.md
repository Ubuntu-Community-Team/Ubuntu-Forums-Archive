---
title: "undeletable file"
date: 2009-11-07
forum: General Help
---

### Post by Colossus121 on 2009-11-07
I tried downloading a torrent file using vuze. I was telling it what files to ignore and then it crashed. I didnt think too much about it and re-tried it. I had to re-add the torrent file. When i did this i noticed it was re-allocating space for the file. i went to check to see if there was a duplicate and sure enough there was. I am unable to delete this duplicate in ubuntu or windows.

I have the file saved to a fat32 partition on my HDD. I had full read/write/delete access in windows and ubuntu but now i only have access in windows. Every time i try to add something to the drive it tells me i don't have access. I am an administrator so i don't understand why this is happening. I went back, re-applied all the permissions in windows but nothing has worked.

please help.

Also I am running 8.04 and Vista(don't judge me)

---

### Post by HereInOz on 2009-11-07
Is the FAT32 partition actually mounted somewhere on the system?

---

### Post by Colossus121 on 2009-11-07
yup. I can look through it, in vista and ubuntu, and have the option to un-mount it as well

---

### Post by x33a on 2009-11-07
Try deleting it using a live cd. not the most elegant solution, but might just work.

---

### Post by Colossus121 on 2009-11-07
> **x33a said:**
> Try deleting it using a live cd. not the most elegant solution, but might just work.

i tried that using the 9.10 CD. no difference.

if there is a live CD that is capable of that then by all means tell me.

---

### Post by x33a on 2009-11-07
do the logs show anything suspiscious?

what does ```
ls -l
```for the file say.

---

### Post by Colossus121 on 2009-11-07
Oh i guess i should have been more specific, it's a directory. but when i try to change to that directory in the terminal all I see is

```
>
```

and nothing else in the line

---

### Post by x33a on 2009-11-07
have you tried
```
rm -rf <dir_name>
```note: be careful with this command. don't use it on any system file or root partiton.

---

### Post by Colossus121 on 2009-11-09
Unfortunately this didnt work either. I still get the same result:

```
>
```

i am completely stuck. As far as I can tell my only option is wiping the partition

---

### Post by bostonblond on 2010-01-26
NoobTip:

I wanted to remove a folder titled Adobe AIR

1.) I opened the Konsole
2.) Typed "sudo -i" (without quotes) so I could work in root
3.) Typed in my password
4.) Typed "cd /opt" so I could **c**hange **d**irectory to the **opt **folder (because that's where my undeleteable file was
5.) Typed  
rm -rf <Adobe AIR>But that didn't work.
6.)So I typed
rm -rf "Adobe AIR"
and my file was deleted.

---

