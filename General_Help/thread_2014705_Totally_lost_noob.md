---
title: "Totally lost noob"
date: 2012-07-02
forum: General Help
---

### Post by KrisKustomPaint on 2012-07-02
Just got Ubuntu and I'm trying to get the wireless network card working. Problem is I'm trying to get to the b43-fwcutter directory but cant seem to find it. I saw the "cd" command and figured it had to work something like dos but i can't figure out how to navigate the directories. The wireless is the only way to get to the internet so I'm stuck shutting down ubuntu, restart, and use windows to get to the internet which makes trying to follow the command lines help a bit challenging.

---

### Post by Elfy on 2012-07-02
It's probably

cd Downloads/b43<tab>

then you can use tab to autocomplete

---

### Post by KrisKustomPaint on 2012-07-02
i typed 
cd Downloads

then i typed
dir

and it just returned the dir like it was empty

---

### Post by bogan on 2012-07-02
Hi!,**KrisCustompaint**,

Try: ```
cd
cd /home/username/Downloads
ls
```Edit: The terminal Prompt will not change, showing if the CD has not been successful.

Chao!, **bogan**.

---

### Post by KrisKustomPaint on 2012-07-02
> **Elfy said:**
> It's probably

cd Downloads/b43<tab>

then you can use tab to autocomplete

Im sure I'm probably doing it worng, but this did nothing

---

### Post by KrisKustomPaint on 2012-07-02
> **bogan said:**
> Hi!,**KrisCustompaint**,

Try: ```
cd
cd /home/username/Downloads
ls
```Edit: The terminal Prompt will not change, showing if the CD has not been successful.

Chao!, **bogan**.

got to the download dir but the "ls" command seemed to do nothing

---

### Post by bogan on 2012-07-02
Hi!,**KrisKustompaint**,

Looks as though there is nothing in Downloads,

Have you tried opening the Home folder and entering 'B43-fwcutter' - or whatever - in the Search box?

When it finds anything,a Right Click on an entry, and selecting 'properties', will show the Path or location.

Chao!, **bogan.**

---

### Post by KrisKustomPaint on 2012-07-02
> **bogan said:**
> Hi!,**KrisKustompaint**,

Looks as though there is nothing in Downloads,

Have you tried opening the Home folder and entering 'B43-fwcutter' - or whatever - in the Search box?

When it finds anything,a Right Click on an entry, and selecting 'properties', will show the Path or location.

Chao!, **bogan.**

No luck again, maybe I'm going about this the wrong way, all I really want is to get my wireless card working in Ubuntu. But all the tutorials and help guide commands don't always work and then I'm just stuck going around in circles like this, shut down restart try one command...nothing, shut down start windows, scribble down the next set of commands to try, shut down, start ubuntu....repeat for 8 hours

---

### Post by holycow131415 on 2012-07-02
May seem silly to ask, but have you plugged your laptop to a wired connection to run the additional drivers program? If you have, then at least youd be able to get online while still in ubuntu to work with this issue via the wired connection.

---

### Post by mkstallings1 on 2012-07-02
If you have an install disc you might want to try this site:
[URL="http://acervulus.info/2011/install-wireless-network-card-driver-without-existing-internet-connection-ethernet-or-usb/"]
http://acervulus.info/2011/install-wireless-network-card-driver-without-existing-internet-connection-ethernet-or-usb/[/URL]

As far as what you have already done; are you sure that what you are looking for is in Downloads?

---

### Post by IWantFroyo on 2012-07-02
> **holycow131415 said:**
> May seem silly to ask, but have you plugged your laptop to a wired connection to run the additional drivers program? If you have, then at least youd be able to get online while still in ubuntu to work with this issue via the wired connection.

+1, was about to post this.

There's a driver for b43- cards in Additional Drivers. You just have to plug into ethernet to run it.

---

### Post by KrisKustomPaint on 2012-07-02
> **holycow131415 said:**
> May seem silly to ask, but have you plugged your laptop to a wired connection to run the additional drivers program? If you have, then at least youd be able to get online while still in ubuntu to work with this issue via the wired connection.

Not an Option

> **mkstallings1 said:**
> If you have an install disc you might want to try this site:
[URL="http://acervulus.info/2011/install-wireless-network-card-driver-without-existing-internet-connection-ethernet-or-usb/"]
http://acervulus.info/2011/install-wireless-network-card-driver-without-existing-internet-connection-ethernet-or-usb/[/URL]

As far as what you have already done; are you sure that what you are looking for is in Downloads?

No intall disk, I downloaded and used the windows installer. Im not sure i even have the files but i have no idea how to find them. After more digging i think i need the STA drivers.

---

### Post by IWantFroyo on 2012-07-02
If you really can't use Ethernet...

[http://packages.debian.org/squeeze/b43-fwcutter](http://packages.debian.org/squeeze/b43-fwcutter)

1) Download the correct architecture of the package (if your install is 32 bit, i386, if 64 bit, amd64).

2) ```
cd Downloads
```

3) ```
ls
``` This command will display the names of everything in the Downloads folder. Look for the driver you just downloaded.

4) ```
sudo dpkg -i *filename*
```

---

### Post by KrisKustomPaint on 2012-07-02
i think part of the problem is this, I can see the folders that everyone is talking about in windows, but when i start ubuntu the file structure looks totally different. why can't i get to the c:\ drive? I tried to look in a folder call root and it said i couldn't because i wasn't the owner. I am positive that if I download anything in windows I will not be able to find it when I start Ubuntu, although I'm not sure why.

---

### Post by KrisKustomPaint on 2012-07-02
Is there a way I can download the drivers in windows and get them to ubuntu?

---

### Post by mkstallings1 on 2012-07-02
On my laptop, I have two 100 GB hdd's with Windows XP on one and Ubuntu 12.04 on the other.  When I open nautilus in Ubuntu to look at my file, in the left pane, under devices, is a folder called 100 GB filesystem.  When I click on that, it takes me to my "C" drive.  Try that and then navigating to your Downloads folder and then copying the file to somewhere on your Ubuntu install.

---

### Post by KrisKustomPaint on 2012-07-02
> **mkstallings1 said:**
> On my laptop, I have two 100 GB hdd's with Windows XP on one and Ubuntu 12.04 on the other.  When I open nautilus in Ubuntu to look at my file, in the left pane, under devices, is a folder called 100 GB filesystem.  When I click on that, it takes me to my "C" drive.  Try that and then navigating to your Downloads folder and then copying the file to somewhere on your Ubuntu install.
I only have one hdd, and when i open nautilus there are only two devices listed one hdd and the dvd drive. the hdd has some thing that says shortcut to c: but when i click on it an error comes up
i think it said unknown file type, its .lnk file

---

### Post by IWantFroyo on 2012-07-02
There is no "C" drive in Ubuntu.

To navigate to the root directory you have to use "sudo."

Easy way to do this:

```
gksudo nautilus
```

---

