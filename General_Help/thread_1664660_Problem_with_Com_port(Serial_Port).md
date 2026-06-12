---
title: "Problem with Com port(Serial Port)"
date: 2011-01-11
forum: General Help
---

### Post by reddog801 on 2011-01-11
Hello Everyone,

First off I'd like to say I'm still very new to the idea of linux and so far I am enjoying what Ubuntu has to offer. However, I'm here because of a small issue(or at least I hope it is).

Allow me to explain what I have going on:


I'm using Ubuntu 10.10 Maverick Meerkat. I have a program called "Ham Radio Deluxe". It is a piece of software that is for Ham Radio Operators and it allows us to hook up our radio's through a serial cable(db9).  I have WINE installed and have effectively download the software and have it running with no problems. When I open the software(HRD) it wants to know the make and model of my radio and what port it will be using. That is where I'm running into problems. I tell it to use the "auto" format and it searches through all the com ports and does not find that the db9 cable is hooked up and therefore will not connect to the radio. 

I have searched high and low for a way to test the com port(serial port) with no luck. I thought I had one way but someone said I needed to have permission. When I try to tell it to give me the permission it still says no. 

Without going off the deep end on me, is there anyone that could possibly help me, keeping in mind I'm still a newbie at all of this, but can follow directions very well. 

Thanks much,

Eric

---

### Post by tredegar on 2011-01-11
I don't use wine, but see [here]("http://www.yolinux.com/TUTORIALS/LinuxTutorialRunMicrosoftExe.html") and scroll down to "Wine Configuration"

Basically you need to make a link from your (linux) serial port (probably **/dev/ttyS0** but check) to the **~/.wine/dosdevices** directory:
```
ln  -s  /dev/ttyS0   ~/.wine/dosdevices/com1
```

---

### Post by reddog801 on 2011-01-11
> ln  -s  /dev/ttyS0   ~/.wine/dosdevices/com1

OK...I'm making small steps and little progress. When I run that command now, I get "creating symbolic link /home/eric/.wine/dosdevices/com1 : File exists"

So this is good right? However when I open the software and choose my radio and chose the com port 1 it throws an Error basically saying Access denied on com1.

I seen that there is something else I need to do to tell the above command to stay in place because if I restart my machine it will default back to what it was. However, before even getting to that I need the software to see the com port...

---

### Post by tredegar on 2011-01-11
OK, some progress.

We need to find out who owns **/dev/ttyS0**

Please post the output of the following commands
```
ls -l /dev/ttyS0
groups
```
On 10.04 **/dev/ttyS0** is owned by root but read and writeable by members of the **dialout** group (of which I am already a member).

If you do not see **dialout** listed as one of your groups, add yourself to that group:
System, Admin, Users & Groups. 

Make the change, logout & back in again for it to be effected.

Check again with the **groups** command, **dialout** should be listed as one of your groups.

If so, time to try again with wine.

---

### Post by reddog801 on 2011-01-12
> ls -1 /dev/ttyS0


This command does nothing for me, if I add groups at the end then it says cannot access groups : No such file or directory. I treid in $ and in root...

---

### Post by reddog801 on 2011-01-12
> ls -1 /dev/ttyS0


This command does nothing for me, if I add groups at the end then it says cannot access groups : No such file or directory. I tried in $ and in root...

---

### Post by reddog801 on 2011-01-12
but when going to System > Admin > Users and Groups  My full name pops up. I clicked on the Manage Groups and dialout is included in the list of others....

---

### Post by reddog801 on 2011-01-12
After going into the users and groups, I checked the box on dialout, then restarted. 

ls -1 /dev/ttyS0 yields :

/dev/ttyS0(highlighted in yellow and green)

groups : 

eric adm dialout cd rom plugdev lpadmin netdev admin sambashare

---

### Post by tredegar on 2011-01-12
If you look carefully at my post at number 4, you see that the command is **ls -l** (read as "Ell Ess Minus Ell" and NOT "Ell Ess Minus One".

Please try again.

At least you are now in the dialup group, right?

---

### Post by tredegar on 2011-01-12
Double-post

---

### Post by tredegar on 2011-01-12
Triple-post, some system failure.

---

### Post by reddog801 on 2011-01-12
OK...

ls -l /dev/ttyS0 yields :


crw-rw---- 1 root dialout 4, 64 2011-01-12 1527 /dev/ttySO(/dev/ttyS0 is highlighted in yellow and green)


Eric

---

### Post by reddog801 on 2011-01-12
Prior to asking for help here...I also done the following command...


ln -s /dev/ttyS0 ~/.wine/dosdevices/com1

It says the file exists, however the software still will not connect to the radio via (db9 cable) and serial/com port...


Eric

---

### Post by reddog801 on 2011-01-12
**UPDATE!**

I was fooling around with a couple more commands and for whatever reason was able to get it to work. The software connected with the radio!

However, once the program is connected, about 15 seconds later BugTrap detects a crash....

Exception Reason :

HamRadioDeluxe.exe caused ACCESS_VIOLATION in module "C:\Program Files\Amateur Radio\Ham Radio Deluxe\HamRadioDeluxe.ext" at 0073:006C6CE2

I'm assuming that I'm going to now need to go over to the Ham Radio Deluxe forums and find out what exactly this means. There are only a few operators using linux for HRD.....

If you can help, that would be awesome. If you cannot then I understand and I thank you for your help that you have given me. I'm still not totally sure what I did other than change the baud settings .....

Thanks!


Eric

---

### Post by reddog801 on 2011-01-12
OK...well somethings are starting to go right.....

I restarted the box and restarted Ham Radio Deluxe. Connected to the radio just fine and not giving me any errors....

So as it stands right now, I'm good I think!


[COLOR="Blue"]EDIT : 

Nope I jumped the gun. Changed frequencies on the radio and then the software threw the crash back up at me!

Any suggestions?[/COLOR]

---

### Post by tredegar on 2011-01-13
Sorry. I don't run wine and don't use win, so all I can help with is sorting out linux permissions, and that issue seems to be fixed.

I understand that not everything runs properly on wine, and sometimes you just need to use a windows computer.

Best wishes.

---

### Post by reddog801 on 2011-01-13
Tredegar,

Very thankful for your help. One more question then I suppose you could close this and mark it solved. What would you recommend in place of WINE?

Obviously I would have to remove WINE if I use something else correct?(sorry again for the newbie questions).

Also, this is a complete ubuntu install on a 250gb hard drive with no windows at all. 


Thanks again for your help, it is definatly appreciated.


Eric

---

### Post by tredegar on 2011-01-13
Wine can run _some_ windows programs.

Windows can run windows programs (although this is debatable).

It is likely that your radio's manual will tell you what the serial  protocols it uses are. In which case, it should be simple to send / listen for the correct control sequences. Eg **echo -en "\033\055" > /dev/ttyS0** sends the octal characters 033  055 (ASCII [COLOR="Red"]ESC-[/COLOR]) to the port. Don't forget that you'll need to set the port up with **stty** to set baud, parity, stop-bits etc. before you try to use it.

You may find **gkermit** an easier way to talk to your radio. More on kermit [here]("http://www.columbia.edu/kermit/kermit.html")

If this is not the case (and I'd be surprised) your only other alternative is to sniff the serial port data traffic to determine the protocols windows uses to communicate with your radio. This *may* not be as difficult as it sounds, and as a radio ham you should have no trouble constructing the necessary hardware.

Then you could gain fame (if not fortune) by releasing the details to the linux community.

You don't *need* to remove wine. My PCs are full of stuff I  installed, used once, then never again.

BTW, only _you_ can mark this thread as "solved".

Have fun & good luck.

---

