---
title: "Dont know why this is hapening"
date: 2010-05-03
forum: General Help
---

### Post by cyberjar09 on 2010-05-03
I always thught this issue would resolve itself when i upgraded from karmic koala to 10.04 but it still persists..!

I have uploaded a video of the problem on rapidshare for your reference.

[http://rapidshare.com/files/383179113/out.avi.html](http://rapidshare.com/files/383179113/out.avi.html)
 MD5: C5D0695C47338D85F88A2DCABC40C859  

Im a complete n00b so please help me. This problem is really hampering my Ubuntu experience. :confused:

my system config is in a html file which is not a valid format for attachment on this forum (???) and hance i have uploaded that too (sysconfig.html)

[http://rapidshare.com/files/383183058/sysinfo.html](http://rapidshare.com/files/383183058/sysinfo.html)
 MD5: CBB7BC18C4A6F14B1CF70F2D9F74C337  

Thanks again.

---

### Post by conradin on 2010-05-03
Ugh yeah, Rapid Share, Im not touching it. Perhaps describe this error, post it to youtube, or something. As for your html, Im not sure why you're doing it that way, how about posting the plain text to a code box?
EDIT:
Your html is just the code for lshw.
here is a simple way to get that code to the forums. 
type:
```

sudo lshw >file

```
then open the file:
```

gedit file

```
The paste that between some [code] brackets.

---

### Post by TeoBigusGeekus on 2010-05-03
Start Firefox, or Eclipse, or anything via command line, repeat the procedure and post us any error messages.

---

### Post by cyberjar09 on 2010-05-03
> **conradin said:**
> Ugh yeah, Rapid Share, Im not touching it. Perhaps describe this error, post it to youtube, or something. As for your html, Im not sure why you're doing it that way, how about posting the plain text to a code box?

sorry for the trouble, but i had to go all the way to my neighbours house to use his comnputer to upload the videos as everytime i click on a "browse" box the application force closes on me! i have provided the MD5 checksum values for verification.

please help..

---

### Post by cyberjar09 on 2010-05-03
> **TeoBigusGeekus said:**
> Start Firefox, or Eclipse, or anything via command line, repeat the procedure and post us any error messages.

I tried to start eclipse by doing as follows

cyber@cyber-desktop:~$ cd eclipse
cyber@cyber-desktop:~/eclipse$ eclipse
The program 'eclipse' is currently not installed.  You can install it by typing:
sudo apt-get install eclipse-platform
cyber@cyber-desktop:~/eclipse$ ls
about_files    eclipse             hs_err_pid2725.log  icon.xpm         readme
about.html     eclipse.ini         hs_err_pid3254.log  libcairo-swt.so
artifacts.xml  epl-v10.html        hs_err_pid5002.log  notice.html
configuration  features            hs_err_pid6782.log  p2
dropins        hs_err_pid2073.log  hs_err_pid6877.log  plugins



What now..?

---

### Post by oldos2er on 2010-05-03
Did you try what it said? ```
sudo apt-get install eclipse-platform
```

---

### Post by TeoBigusGeekus on 2010-05-03
Forget eclipse... Try firefox. Just open the terminal, type firefox and press enter. Do the browse thing and after firefox disappears, you should be able to see error messages.

---

### Post by spoon_ on 2010-05-03
> **cyberjar09 said:**
> I tried to start eclipse by doing as follows

cyber@cyber-desktop:~$ cd eclipse
cyber@cyber-desktop:~/eclipse$ eclipse
The program 'eclipse' is currently not installed.  You can install it by typing:
sudo apt-get install eclipse-platform
cyber@cyber-desktop:~/eclipse$ ls
about_files    eclipse             hs_err_pid2725.log  icon.xpm         readme
about.html     eclipse.ini         hs_err_pid3254.log  libcairo-swt.so
artifacts.xml  epl-v10.html        hs_err_pid5002.log  notice.html
configuration  features            hs_err_pid6782.log  p2
dropins        hs_err_pid2073.log  hs_err_pid6877.log  plugins



What now..?


You have to start it with the command "./eclipse" instead of "eclipse" because bash by default does not search "." (the current directory).

---

### Post by cyberjar09 on 2010-05-03
> **conradin said:**
> Ugh yeah, Rapid Share, Im not touching it. Perhaps describe this error, post it to youtube, or something. As for your html, Im not sure why you're doing it that way, how about posting the plain text to a code box?
EDIT:
Your html is just the code for lshw.
here is a simple way to get that code to the forums. 
type:
```

sudo lshw >file

```
then open the file:
```

gedit file

```
The paste that between some [code] brackets.

I tried the above with and without file extensions. Im unable to open the file

Could not open the file /home/cyber/sysinfo.log.
gedit has not been able to detect the character encoding.
Please check that you are not trying to open a binary file.
Select a character encoding from the menu and try again.


Could not open the file /home/cyber/sysinfo.

Could not open the file /home/cyber/sysinfo.txt

---

### Post by cyberjar09 on 2010-05-03
> **oldos2er said:**
> Did you try what it said? ```
sudo apt-get install eclipse-platform
```

its redownloading eclipse now..! =(

---

### Post by cyberjar09 on 2010-05-03
> **TeoBigusGeekus said:**
> Forget eclipse... Try firefox. Just open the terminal, type firefox and press enter. Do the browse thing and after firefox disappears, you should be able to see error messages.

No I launched firefox from terminal and it force closed but no error in terminal ... y is this happening to me...?!

---

### Post by cyberjar09 on 2010-05-03
> **spoon_ said:**
> You have to start it with the command "./eclipse" instead of "eclipse" because bash by default does not search "." (the current directory).

ok i got this for you guys... hope its helpful

cyber@cyber-desktop:~$ cd eclipse
cyber@cyber-desktop:~/eclipse$ ./eclipse
#
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x01089f80, pid=4410, tid=3077920448
#
# JRE version: 6.0_20-b02
# Java VM: Java HotSpot(TM) Client VM (16.3-b01 mixed mode, sharing linux-x86 )
# Problematic frame:
# C  [libgtk-x11-2.0.so.0+0xeaf80]
#
# An error report file with more information is saved as:
# /home/cyber/eclipse/hs_err_pid4410.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
# The crash happened outside the Java Virtual Machine in native code.
# See problematic frame for where to report the bug.
#
Aborted
cyber@cyber-desktop:~/eclipse$

---

### Post by TeoBigusGeekus on 2010-05-03
Very strange indeed...
To tell you the truth, I've always had trouble upgrading - the only thing I could suggest, is a backup and a nice clean install of Lucid. 
A broken package in Karmic is bound to stay broken after an upgrade...
Sorry for the no help...

---

### Post by cyberjar09 on 2010-05-03
ok as far as eclipse is concerned, i think its a jvm problem ... 

I think a good option would be to reinstall the OS now..?

---

### Post by cyberjar09 on 2010-05-03
> **TeoBigusGeekus said:**
> Very strange indeed...
To tell you the truth, I've always had trouble upgrading - the only thing I could suggest, is a backup and a nice clean install of Lucid. 
A broken package in Karmic is bound to stay broken after an upgrade...
Sorry for the no help...

But i did do a complete format and reinstall ... i had the same problem with my karmic koala ...is it a H/W related issue? maybe faulty ram?

---

### Post by TeoBigusGeekus on 2010-05-03
> **cyberjar09 said:**
> ok as far as eclipse is concerned, i think its a jvm problem ... 

I think a good option would be to reinstall the OS now..?
In my opinion yes - unless someone wiser has something else to propose.
Never do an upgrade - perform a clean install while keeping a separate home partition: whenever you reinstall use this partition, that way you can have all your settings back.
EDIT:
Sorry, just read your last post...
I was under the impression that you upgraded from Karmic.
Totally WTF problem...
Errr.... someone else?

---

### Post by cyberjar09 on 2010-05-03
please help...! :(

---

### Post by cyberjar09 on 2010-05-03
> **TeoBigusGeekus said:**
> In my opinion yes - unless someone wiser has something else to propose.
Never do an upgrade - perform a clean install while keeping a separate home partition: whenever you reinstall use this partition, that way you can have all your settings back.
EDIT:
Sorry, just read your last post...
I was under the impression that you upgraded from Karmic.
Totally WTF problem...
Errr.... someone else?

keep a separate home partition..?! pls point me in the right direction (link) ... where can i read about this method of installing.?

---

### Post by TeoBigusGeekus on 2010-05-03
> **cyberjar09 said:**
> keep a separate home partition..?! pls point me in the right direction (link) ... where can i read about this method of installing.?
Whenever you install, choose manual partitioning. There, create a separate partition, to be mounted as /home - size according to your needs.
During reinstalling, choose manual partitioning again, give the same partition to be used as /home, but DON'T format.
Thus, all your previous settings will be kept. For example, lets say you had Thunderbird installed. You decide to reinstall Ubuntu, keeping your old /home partition. The fresh install doesn't have Thunderbird, so you install it. When you open it, you will be pleasantly surprised to see all your settings, addresses, emails, etc. untouched from Ubuntu's reinstallation.

---

### Post by cyberjar09 on 2010-05-03
> **TeoBigusGeekus said:**
> Whenever you install, choose manual partitioning. There, create a separate partition, to be mounted as /home - size according to your needs.
During reinstalling, choose manual partitioning again, give the same partition to be used as /home, but DON'T format.
Thus, all your previous settings will be kept. For example, lets say you had Thunderbird installed. You decide to reinstall Ubuntu, keeping your old /home partition. The fresh install doesn't have Thunderbird, so you install it. When you open it, you will be pleasantly surprised to see all your settings, addresses, emails, etc. untouched from Ubuntu's reinstallation.

ok this seems fairly straight forward, but i store all my data in my user home folder, approx how much space should i allocate to the /home partition?

EDIT
up until now i have always used the "/" option when installing ...

---

### Post by cyberjar09 on 2010-05-03
thank you so much everyone for your help. 

TeoBigusGeekus, ill use the method u just told me about to reinstall now. 

But this still does not resolve the issue because this is a recurring event on my PC ... I need to figure out whats really causing the force close. 

Thanks again.

---

### Post by TeoBigusGeekus on 2010-05-03
> **cyberjar09 said:**
> ok this seems fairly straight forward, but i store all my data in my user home folder, approx how much space should i allocate to the /home partition?
Depends actually. The best answer is as much as you want :)
I, for example, have a 20GB root partition (the only part of my hd that's formatted when I reinstall), a 50GB home partition and 2 other ~500GB partitions for data storage.

---

### Post by TeoBigusGeekus on 2010-05-03
Before reinstalling check your cd for defects...
Good luck mate...

---

### Post by cyberjar09 on 2010-05-03
> **TeoBigusGeekus said:**
> Before reinstalling check your cd for defects...
Good luck mate...

ok now i am really confused.! ... I for instance have 1 partition for swap space and 1 partition where i use the "/" option with ext4 file system where ubuntu is installed. 

Can you send me a link i can refer to with your method of installation? 

and about the cd, I did a verification when i burnt it. 

Thanks.

---

### Post by TeoBigusGeekus on 2010-05-03
My full partition table:
swap: 1Gb
/ 20Gb (the / mount point designates root - the only partition you need to format whenever you reinstall)
/home 50Gb (the home partition - during reinstallation, give this partition to be mounted on mount point /home but DON'T format it)
/media/disk 500Gb (data storage)
/media/disk-1 300Gb (the same).

About checking the cd for defects:
When you boot with the ubuntu cd, press any key when you see the keyboard icon at the bottom of your screen. You will be taken to a menu where you can choose the language of the UI, whether you want to install or just try Ubuntu, etc. One option is to check the cd for defects. That's what I'm talking about...

---

### Post by cyberjar09 on 2010-05-03
ok got it thanks ill do it... now alalready 60% done with the install.. ill check back l8r.

EDIT
one more quick question, karmic koala gave me the option of a full destination or path to a particular folder when I clicked on the pencil button. How do I get that in lucid lynx..?

---

### Post by TeoBigusGeekus on 2010-05-03
> **cyberjar09 said:**
> one more quick question, karmic koala gave me the option of a full destination or path to a particular folder when I clicked on the pencil button. How do I get that in lucid lynx..?
Could you be a bit more specific? I've no idea of what you're talking about...

---

### Post by cyberjar09 on 2010-05-03
Sorry... when u go to places >computer for instance, the blocks that show your navigation history used to have a small pencil logo next to them. ...if u were to click on them, u would get the complete path to the current directory in text format.. got it..?

---

### Post by TeoBigusGeekus on 2010-05-03
> **cyberjar09 said:**
> Sorry... when u go to places >computer for instance, the blocks that show your navigation history used to have a small pencil logo next to them. ...if u were to click on them, u would get the complete path to the current directory in text format.. got it..?
Oh, right... Just click Ctrl-L.

---

### Post by cyberjar09 on 2010-05-03
Ok done resting the disk now running a memory test. Hope all is well here.

I don't know if this is a problem but I initially had 2gb of 800mhz corsair ram. I recently added another single 2gb ram from kingston (667mhz). So now 3 out of 4 slots are used and my 4 gig ram runs at 667. Could this be the problem..?

---

### Post by TeoBigusGeekus on 2010-05-03
> **cyberjar09 said:**
> Ok done resting the disk now running a memory test. Hope all is well here.

I don't know if this is a problem but I initially had 2gb of 800mhz corsair ram. I recently added another single 2gb ram from kingston (667mhz). So now 3 out of 4 slots are used and my 4 gig ram runs at 667. Could this be the problem..?
No idea...

---

### Post by cyberjar09 on 2010-05-03
Ok either way I'm running a memtest now so that ought to shed some light on my question... thanks a bunch again. :-):D

---

