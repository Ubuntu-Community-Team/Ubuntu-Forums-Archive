---
title: "Truecrypt does not install"
date: 2010-11-07
forum: General Help
---

### Post by abexs on 2010-11-07
Hi,  I checked out this forum but still no solution for my problem.  I'm new to Ubuntu and linux, I tried to install Truecrypt, but I can't get it fixed.  I extracted truecrypt-7.0a-setup-x64 to Desktop.  Then in typed in terminal: sudo sh truecrypt-7.0a-setup-x64.  The terminal asks my password and I type in my password and hit enter.  The terminal disappears and nothing is happening. Who can help me out?

---

### Post by gandaran on 2010-11-07
easy way to install truecrypt is to first right click the file, go to properties » permission tab, check-mark the execute file box then just double click the file and choose run to open the install window.

---

### Post by abexs on 2010-11-07
@gandaran  I already tried that and I got the following error:  Failed to run ... The underlying authorization mechanism (sudo) does not allow ...

---

### Post by gandaran on 2010-11-07
> **abexs said:**
> @gandaran  I already tried that and I got the following error:  Failed to run ... The underlying authorization mechanism (sudo) does not allow ...
which truecrypt package did you download, the standard or console?

---

### Post by abexs on 2010-11-07
The standard package

---

### Post by karthick87 on 2010-11-07
You can find a nice **How to Guide **below for installing tryecrypt

[http://ubuntuforums.org/showthread.php?t=149561](http://ubuntuforums.org/showthread.php?t=149561)

---

### Post by gandaran on 2010-11-07
I just done the download and installed it again this way (the file run option is disabled in my system) right click the file and choose 'open with other application' in the command box fill in 'xterm' then just click open and the install window will open.

---

### Post by abexs on 2010-11-07
@gandaran  I tried it your way and I  get:  Failed to run tar '-C' '/' '-xpzvf' '/tmp/truecrypt_7.0a_amd64.tar.gz' as user root. The underlying authorization mechanism (sudo) does not allow you to run this program. Contact the system administrator.

---

### Post by abexs on 2010-11-07
@getyourkarthick  That's like mandarin chinese for me-

---

### Post by gandaran on 2010-11-07
> Failed to run tar '-C' '/' '-xpzvf' '/tmp/truecrypt_7.0a_amd64.tar.gz
well, you are trying to install a tar.gz package! you have to extract the package first and run the extracted file after marking it executable in properties » permissions tab.

---

### Post by abexs on 2010-11-07
I did extract the package and got truecrypt-7.0a-setup-x64. Then I follow your instructions and get that error, weird.  When I select "Extract tar package" in the installation menu of Truecrypt, it extracts files to tmp as tar package. In that package I see usr folder.

---

### Post by gandaran on 2010-11-07
> I did extract the package and got truecrypt-7.0a-setup-x64. Then I follow your instructions and get that error, weird. When I select "Extract tar package" in the installation menu of Truecrypt, it extracts files to tmp as tar package. In that package I see usr folder.
so you did get to the install window! 
if you want to install choose the install option not the extract option!

---

### Post by abexs on 2010-11-07
When I do that, after I entered my password the terminal closes and is gone. 
Nothing happens. I'm getting desperate by Ubuntu... lol

---

### Post by gandaran on 2010-11-07
> **abexs said:**
> When I do that, after I entered my password the terminal closes and is gone. 
Nothing happens. I'm getting desperate by Ubuntu... lol
do what? where do you enter the password in terminal or gksudo dialogue window?

---

### Post by gandaran on 2010-11-07
> **abexs said:**
> Hi,  I checked out this forum but still no solution for my problem.  I'm new to Ubuntu and linux, I tried to install Truecrypt, but I can't get it fixed.  I extracted truecrypt-7.0a-setup-x64 to Desktop.  Then in typed in terminal: sudo sh truecrypt-7.0a-setup-x64.  The terminal asks my password and I type in my password and hit enter.  The terminal disappears and nothing is happening. Who can help me out?
reading this again I think I mite know the problem, dont use sudo, just type the run command without the sudo 
```
sh truecrypt-7.0a-setup-x64
```
then choose the install option and enter the password in the gksudo window when it opens.
hope this time it installs.

---

### Post by abexs on 2010-11-07
Ok, I re-read everything.

I have extracted the truecrypt-7.0a-setup-x64 file from the package truecrypt-7.0a-linux-x64.tar.gz
I have put it in home/abexs (abexs is my username)
Permissions are set right.
I tried to run it on all the possible ways like stated here.

I get an error from the Truecrypt installer:
```
Installation/extraction aborted
```

---

### Post by gandaran on 2010-11-07
> **abexs said:**
> Ok, I re-read everything.

I have extracted the truecrypt-7.0a-setup-x64 file from the package truecrypt-7.0a-linux-x64.tar.gz
I have put it in home/abexs (abexs is my username)
Permissions are set right.
I tried to run it on all the possible ways like stated here.

I get an error from the Truecrypt installer:
```
Installation/extraction aborted
```
are you runnig ubuntu 64-bits? your file is for 64-bits only! could this be the problem?

---

### Post by abexs on 2010-11-07
Running 64 bit Ubuntu (to be sure I also checked the 32 bit version of Truecrypt and got the same error).

---

### Post by gandaran on 2010-11-07
> **abexs said:**
> Running 64 bit Ubuntu (to be sure I also checked the 32 bit version of Truecrypt and got the same error).
well sorry then, I cant help you anymore, as you can see there are more than one way to install truecrypt, any one should work, I just don't know what is the problem.
but just one last question, when you click the install button from truecrypt install window don't you get a password window asking for the password? do you type in the password?

---

### Post by abexs on 2010-11-11
Hi,
I found the solution to my problem, my user was not in the sudoers file.
Thank you all for your help.

---

