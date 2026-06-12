---
title: "Help installng metasploit on 10.10 maverick 64 under KDE"
date: 2011-12-07
forum: General Help
---

### Post by Sikez on 2011-12-07
Does anyone have any advice on installing metasploit on 10.10 Maverick under the KDE Desk top.
I have searched relentlessly for the past several days and have found a couple threads on here that were no help at all couldnt even get past the first command line.
However nothing I have found on the web seems to work either.

I want to be able to run both the Gui & also the console under KDE.
I haven't had any problems with getting it to work under backtrack & also a couple versions of windows.
But for some reason I cannot get it to work at all with Ubuntu.

---

### Post by searchfgold6789 on 2011-12-07
Do these downloads work? [http://metasploit.com/download/](http://metasploit.com/download/)
There seems to be a simple .run file, but it's only compatible with 8.04 and 10.04.
Exact error messages?

---

### Post by seawolf167 on 2011-12-07
Looks like there are decent installation instructions that can be found here:
[https://community.rapid7.com/docs/DOC-1296](https://community.rapid7.com/docs/DOC-1296)

and here:
[https://community.rapid7.com/docs/DOC-1293](https://community.rapid7.com/docs/DOC-1293)

Have you tried following those yet?

---

### Post by Sikez on 2011-12-07
> **searchfgold6789 said:**
> Do these downloads work? [http://metasploit.com/download/](http://metasploit.com/download/)
There seems to be a simple .run file, but it's only compatible with 8.04 and 10.04.
Exact error messages?

Downloaded the 64 bit version for metasploit-latest-linux-x64-installer.run
Tried the run file.... and got a windows alert error in a wine pop up alert.

No luck with the tar The tar-ball either.

Also tried an auto install script a friend made for me that should have made it simple,but that wouldn't work either.

---

### Post by seawolf167 on 2011-12-07
> **Sikez said:**
> Tried the run file.... and got a windows alert error in a wine pop up alert.

Why did you open in with Wine? Try just making the .run file executable then running it

```
cd /path/to/file/directory
sudo chmod +x filename.run
./filename.run
```

Change the above path and filename to match where you saved the file and what its name is

---

### Post by Sikez on 2011-12-07
> **seawolf167 said:**
> Looks like there are decent installation instructions that can be found here:
[https://community.rapid7.com/docs/DOC-1296](https://community.rapid7.com/docs/DOC-1296)

and here:
[https://community.rapid7.com/docs/DOC-1293](https://community.rapid7.com/docs/DOC-1293)

Have you tried following those yet?

Thanks..
But already tried both of those....no luck.

---

### Post by Sikez on 2011-12-07
> **seawolf167 said:**
> Why did you open in with Wine? Try just making the .run file executable then running it

```
cd /path/to/file/directory
sudo chmod +x filename.run
./filename.run
```Change the above path and filename to match where you saved the file and what its name is

I didn't open it with wine....
For some reason when the DL completed for some reason it automatically does it.

Thanks for the info though.

---

### Post by seawolf167 on 2011-12-07
> **Sikez said:**
> I didn't open it with wine....
For some reason when the DL completed for some reason it automatically does it.

Thanks for the info though.

Were you able to run it successfully through the terminal?

---

### Post by Sikez on 2011-12-07
> **seawolf167 said:**
> Were you able to run it successfully through the terminal?
  
No I get this message "Error is not recoverable: exiting now"

---

### Post by seawolf167 on 2011-12-07
Try re-downloading the file again and then run it through the terminal. Sounds like the file may have been corrupted. If there is an [MD5SUM ]("https://help.ubuntu.com/community/HowToMD5SUM")available, use it to check the download's integrity.

---

