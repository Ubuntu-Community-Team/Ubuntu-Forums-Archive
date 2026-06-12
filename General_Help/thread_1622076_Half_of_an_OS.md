---
title: "Half of an OS"
date: 2010-11-15
forum: General Help
---

### Post by Red Scope53 on 2010-11-15
I was installing Ubuntu, as a program, so I could have both my windows XP and Ubuntu, but I think it tried to install its self as the only OS and wiped part of Windows. It had many errors while installing. It kept showing a bunch of error codes and wasn't doing anything, so I shut off my PC by the button. When I booted it back up, it just kept restarting right before it showed the user accounts. I got it to run in safe mode, but there was no task bar or icons( kind of like I closed the "explorer.exe" in task manager)*<edit: see first image>*

But when going into the C>WINDOWS, there is NO explorer.exe, and it looks like alot of things are missing. I'm worried sick I messed up the only working PC we have now, since my laptop died 3 days ago and we have no idea why. Any one here have any ideas?

My windows folder in my C-drive
*<edit: see second image>*


Click>>[I'm also posting this on the Microsoft website]("http://social.answers.microsoft.com/Forums/en-US/xphardware/thread/c5a03030-6d3f-493a-b875-46a7d3cbea83")<<Click

---

### Post by lisati on 2010-11-15
How were you installing? As a "dual boot" or with Wubi?

---

### Post by Verbeck on 2010-11-15
the wubi installer creates a virtual disk in c/ubuntu. it cant install it self as the only os unless booted from the cd

do you recall what error the installer gave?

---

### Post by Red Scope53 on 2010-11-15
@lisati: I guess as a dual boot. I burned in onto a cd on my laptop, then stuck it in my desktop cd drive, booted it up, and it showed the copy rights, then showed this ( see below)


 **I also tried** installing it on my other laptop(the one that died) and I got as far as the screen with the thing that looks like a film strip and the = sign with the man in the circle on each others right, but it then just sits there..doing nothing.. or moving.. I have friends that use Ubuntu, and they say its broken because the download or burning processes got messed up. 

@Verbeck: They all looked about the same( the font was tiny, green and stretched) 

ALSO. 1. At least I can save all my stuff, because I can get it to come on, and can copy them to a flash drive. 2 It never showed an installer. I don't know why, but it went from booting up, to the picture of the little man in the circle. Never asked me or anything.

---

### Post by nlsthzn on 2010-11-15
Sounds like your friends where most probably right about the burn... either the download is corrupt or the burn went bad... however, installing in this manner would either destroy your partition which had Windows (which means all files would be gone) or leave it be... not have some files missing :confused:
 
(Pity we don't know what the error messages where you got...)

---

### Post by Red Scope53 on 2010-11-15
Well, like I said, I can't find explorer.exe any more, and It looks like files are missing from the windows folder. I'm busy using task manager to swich tabs and open programs and such, and even to copy my stuff to my flash drive, as I can't very well open up My Computer any more :\

---

### Post by Verbeck on 2010-11-15
if it didn't get past that screen, then i doubt that ubuntu got installed..
you friends might be right, try checking the md5 sum of the downloaded iso

to check from ubuntu, open a terminal (applications>accessories>Terminal) then type **md5sum **followed by a space, then click and drag the iso you downloaded from the folder to the terminal window and hit enter
so the command looks like [B]md5sum '/path/to/iso.iso'
[/B]
from windows, try the instructions at [https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM%20on%20Windows](https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM%20on%20Windows)
 
it should output the md5sum
compare it to [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes) and see whether its a good download or not..

---

### Post by Red Scope53 on 2010-11-15
Im not sure how, Also, I'm not sure which one I downloaded :\

---

### Post by Verbeck on 2010-11-15
the file name of the downloaded iso will be the same at [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

for example, ubuntu-10.10-desktop-i386.so

---

### Post by Red Scope53 on 2010-11-15
> **Verbeck said:**
> if you're not sure which one you downloaded, the file name of the downloaded iso will be there at [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

for example, ubuntu-10.10-desktop-i386.so

I mean I'm not sure which Ubuntu I have. I also found this on Google, as you can see, a few things are added, and the 'explorer.exe' is clearly missing from mine.

---

### Post by Verbeck on 2010-11-15
well, if you don't have a windows repair disk, there's a temporary replacement for explorer until you can find a fix (its a separate program). its  not as user-friendly as the default browser but can do its job

you can get it from [here]("http://www.zabkat.com/x2lite.htm") 
the portable version [http://usb.smithtech.us/apps/xplorer2lite.php](http://usb.smithtech.us/apps/xplorer2lite.php)

more on it: [http://en.wikipedia.org/wiki/Xplorer%C2%B2]("http://en.wikipedia.org/wiki/Xplorer%C2%B2")

---

### Post by mastablasta on 2010-11-15
i think you can always repair windows with Windows CD.

---

### Post by nlsthzn on 2010-11-15
It is sad when something like this happens... I hope that OP does not just assume "Ubuntu" or "Linux" did this as it really gives a lot of negative light when non is warranted... 
 
Secondly I truly hope you get all your files backed up (always a good idea before installing something like a second OS) and that he does try again after a little more research into how-to do it successfully...

---

### Post by Red Scope53 on 2010-11-15
It seems that only explorer.exe is missing. I don't have a XP cd as it came installed (they should so change that)I don't have the money to buy a new xp cd, and my family has stuff on this computer, so I really can't wipe it without making some one mad... Sigh, I hate computers.

---

### Post by TNT1 on 2010-11-15
sorry, maybe I misunderstand, but can you use the windows os? Or is it not booting?

---

### Post by theozzlives on 2010-11-15
The screenshots you're displaying shows you using the Windows Explorer. That's explorer.exe. Internet Explorer should be under program files (msie.exe).

---

### Post by TNT1 on 2010-11-15
> **theozzlives said:**
> The screenshots you're displaying shows you using the Windows Explorer. That's explorer.exe. Internet explorer should be under program files (msie.exe).

Exactly why I asked if he can get into the windows system, cause windows wont exactly run if explorer.exe is gone...

---

### Post by msandoy on 2010-11-15
I understand that I'm probably entering into a grey zone here, but you do not have to buy a new windows cd. Since you bought the computer with windows pre installed, it should have a sticker on the side or under, telling you the CD-key, and the version installed(Home, pro, etc.). In your case, I would search around, and find a download of the corresponding version. Strictly speaking, you have paid for the licence, and there is nothing in the licence agreement forbiding you to make or use a copy of an original XP CD. The CD-key is your proof of licence ownership.
If you do this, make sure you read up on repair instructions for XP. They can be quite tricky if you have never done this before.

---

### Post by nlsthzn on 2010-11-15
> **msandoy said:**
> I understand that I'm probably entering into a grey zone here, but you do not have to buy a new windows cd. Since you bought the computer with windows pre installed, it should have a sticker on the side or under, telling you the CD-key, and the version installed(Home, pro, etc.). In your case, I would search around, and find a download of the corresponding version. Strictly speaking, you have paid for the licence, and there is nothing in the licence agreement forbiding you to make or use a copy of an original XP CD. The CD-key is your proof of licence ownership.
If you do this, make sure you read up on repair instructions for XP. They can be quite tricky if you have never done this before.
 
You will not *easily* find a legit copy of Windows to download... I faced a problem on my netbook with Windows 7 Starter and after running Ubuntu on it I had to go via the Pirate Bay to get a copy to install my legally bought OS... reason I promptly installed Ubuntu again :D
 
Hope the peeps at the Windows forum is more helpful in getting your Windows back up and running... once it is we can surely help you get Ubuntu on there too...

---

### Post by Verbeck on 2010-11-15
> **theozzlives said:**
> The screenshots you're displaying shows you using the Windows Explorer. That's explorer.exe. Internet Explorer should be under program files (msie.exe).

mm.... he's taking the screenshots using the browse function in task manager. not explorer

---

### Post by TBABill on 2010-11-15
Does XP have the "restore point" feature like Vista did? Can you restore to a previous date BEFORE the Ubuntu install? That would not require the disk, but I can't recall if XP had that functionality.

---

### Post by TNT1 on 2010-11-15
XP does have the restore thingy, but, again, if he can get into the OS from bootup, then he has not deleted the system file he thinks he has.

---

### Post by Red Scope53 on 2010-11-15
@TNT1: Yes actually I have. I do know a-lot about computers, and I even build them. So if I can't find the explorer.exe, it isn't on my computer any more. I can't search my PC as, well, the searcher is an explorer item.. But Its no longer in C>Windows. I honest to God don't see how installing Ubuntu removed the explorer.exe. Maybe I had a virus already( I have NAV [I got it free, I know its not the best] And no, I did get it legally) I've been looking every where for an explorer.exe with no luck. I'll try a few more things. Thanks for all the help.

---

### Post by Red Scope53 on 2010-11-15
> **Verbeck said:**
> well, if you don't have a windows repair disk, there's a temporary replacement for explorer until you can find a fix (its a separate program). its  not as user-friendly as the default browser but can do its job

you can get it from [here]("http://www.zabkat.com/x2lite.htm") 
the portable version [http://usb.smithtech.us/apps/xplorer2lite.php](http://usb.smithtech.us/apps/xplorer2lite.php)

more on it: [http://en.wikipedia.org/wiki/Xplorer%C2%B2]("http://en.wikipedia.org/wiki/Xplorer%C2%B2")
Thank you so much. Of course this can't replace it, and I'll have to end up wiping it anyways, but this makes backing my files up and navigating MUCH easier. (btw, I've been posting on the pc this whole time)

---

### Post by Red Scope53 on 2010-11-15
I've looked every where for a downloadable repair CD, I havn't found one. If any one knows where I can get a fix without wiping, I'd be very happy.

---

