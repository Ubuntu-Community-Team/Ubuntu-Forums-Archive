---
title: "Cups 1.2 or higher required ?"
date: 2009-07-26
forum: General Help
---

### Post by its_jon on 2009-07-26
I recently installed Ubuntu 9.4 on a laptop.... sorted out the wireless chip, thought everything was ok....
however the Lexmark printer is not working...

I have followed these instructions which appear to be full of hope:-
[http://forums.linux-foundation.org/read.php?29,9780,9780](http://forums.linux-foundation.org/read.php?29,9780,9780)

When I run the installer I get the error 

```
The installer has detected the operating system does not meet CUPS minimum version requirements. Please install CUPS version 1.2 or higher and run the installer again.
```

I checked in synaptic and found (or assume) to be running a higher version of Cups
Cups 1,3,9-17 ?????

Help please
John in 
Scotland

---

### Post by nathan726 on 2009-07-31
I had the same problem (Ubuntu 9.04, CUPS version 1.3.9) and I wanted to get my Lexmark X2630 printer working. Do this in the terminal (but change home/nathan/downloads to the path of the .zip you downloaded):

```
cd '/home/nathan/downloads'
unzip 'lexmark-inkjet-08-driver-1.0-1.i386.deb.sh.zip'
./lexmark-inkjet-08-driver-1.0-1.i386.deb.sh --noexec --target lexmark_install

```Now we have extracted the files and you need to fix "is_cups_version_ok" function near the end of the 'lexmark_install/config/run.lua' file. It's quite easy - just open it in a text editor and insert '--[[' and '--]]' like this:

```
function is_cups_version_ok()
    local bRet = true
    [COLOR=Red]--[[[/COLOR]local packager = get_system_packaging()
    local tmp_path = g_mysecurepath
    local busehome = false
    
    if tmp_path ~= nil and os.fileexists(tmp_path) then
         use home        
        if os.fileexists(tmp_path .. '/cups_packages_072006') then
            os.remove(tmp_path .. '/cups_packages_072006')
        end        
        
        if os.fileexists(tmp_path .. '/cups_packages_072006') then        
            tmp_path = install.gettempdir()
        else
            busehome = true
        end        
    else
        tmp_path = install.gettempdir()
    end

    if packager == "rpm" then
        os.execute('rpm -qa|grep cups > ' .. tmp_path .. '/cups_packages_072006')
        cups_packages = shell_execute('cat ' .. tmp_path .. '/cups_packages_072006')
        if cups_packages ~= nil and #cups_packages > 0 then
            for _,cupspackage in pairs(cups_packages) do
                cups_item = hyphen_replace(cupspackage)
                if string.find(cups_item,'cups_1.1.')==1 then
                    bRet = false
                    break
                end
            end
        else
            bRet = false 
        end
    elseif packager == "dpkg" then
        os.execute("dpkg -l | grep cups | awk '{print $2$3}' > " .. tmp_path .. "/cups_packages_072006")
        cups_packages = shell_execute('cat ' .. tmp_path .. '/cups_packages_072006')
        if cups_packages ~= nil and #cups_packages > 0 then
            for _,cupspackage in pairs(cups_packages) do
                cups_item = cupspackage
                if string.find(cups_item,'cups1.1.')==1 or string.find(cups_item,'cupsys1.1.')==1 then
                    bRet = false
                    break
                end
            end
        else
            bRet = false 
        end
    else

    end
    
    if busehome == true then
         os.remove(tmp_path .. '/cups_packages_072006')
    end
    [COLOR=Red]--]][/COLOR]
    return bRet
end
```Now the file is fixed, it's time to install it:
```
cd '/home/nathan/downloads/lexmark_install'
sudo ./startupinstaller.sh
```Note: it will install without checking your cups version. So make sure you have cups version above 1.2 - if you want to find what cups version you have just type 'http://localhost:631/' into your web browser address bar.

---

### Post by afrodeity on 2009-08-01
Great stuff. I think Lexmark patched their X2650 driver. Because they asked me to download it again and assured me it would work on 64bit. Installer runs without the cups problem but clearly does not support 64!!!!!

---

### Post by afrodeity on 2009-08-01
I opened the installer and see that there is some attempt to cater for 64bit architecture

```
CURRENT_ARCH=`uname -m`
    # iX86 --> x86
    echo $CURRENT_ARCH | grep "i.86" >/dev/null && CURRENT_ARCH="x86"

    # Solaris uses i86pc instead of x86 (or i*86), convert
    echo $CURRENT_ARCH | grep "i86pc" >/dev/null && CURRENT_ARCH="x86"   

	# Some platforms use x86_64, some amd64...lets just stick to one :)
	echo $CURRENT_ARCH | grep "amd64" >/dev/null && CURRENT_ARCH="x86_64" # Convert amd64 --> x86_64
	
    echo "CPU Arch: $CURRENT_ARCH"

```

but it doesn't work, just defaults to 32bit and fails to install.

---

### Post by its_jon on 2009-08-12
> Now we have extracted the files, you need to edit "is_cups_version_ok" function in the 'lexmark_install/config/run.lua' file so that it will return true no matter what. Just open it in a text editor and add '--[[' and '--]]' like this:

I only have one file in the archive ?
deb.sh ?

I can not find 'Lexmark_install/config/run.lua ?????????

help :|

---

### Post by nathan726 on 2009-08-12
> **afrodeity said:**
> but it doesn't work, just defaults to 32bit and fails to install.

Sorry, I don't have a clue when it comes to 64bit installs... maybe this driver is 32bit only??

> **its_jon said:**
> I only have one file in the archive ?
deb.sh ?

I can not find 'Lexmark_install/config/run.lua ?????????

help :|

Yep after you extract the .zip file you do have a .sh file, but that ain't the end of the story. The .sh file is an executable archive.
You can extract it's contents - open the terminal and then "cd" to the directory which has your .sh file and extract it's contents using this code, like I mentioned above:
```
./lexmark-inkjet-08-driver-1.0-1.i386.deb.sh --noexec --target lexmark_install
```You will then have all the files extracted to a to the "lexmark_install" folder.

---

### Post by Magic_Spehar on 2009-08-26
I have the same issue.  I switched to Ubuntu 9.04 64 bit I can't do anything with my Lexmark X2650 since the existing driver only works with 32 bit.  I can't use getlibs either since the driver is not .deb but in a script .sh

---

### Post by Magic_Spehar on 2009-09-03
I found the solution for the missing 64 bit linux driver of my Lexmark X2650. I guess there will be an similar solution for all people with a Lexmark X-series printer and a 64-bit Ubuntu system.  
You need a part of the code that Nathan726 used in this thread (thanks for that, by the way...) 

Now, here's the complete solution
---------------------------------
* download lexmark-inkjet-08-driver-1.0-1.i386.deb.sh.zip for Ubuntu 32 bit from the Lexmark website
* unzip 'lexmark-inkjet-08-driver-1.0-1.i386.deb.sh.zip'
* enter in a terminal:  sudo ./lexmark-inkjet-08-driver-1.0-1.i386.deb.sh --noexec --target lexmark_install
* Now go to your directory lexmark_install
* In that directory you'll find a file named arch.tar   Unzip that file.
* Once unzipped you'll find lexmark-inkjet-08-driver-1.0-1.i386.deb
* Ok, now download and install the program getlibs from [http://frozenfox.freehostia.com/cappy/](http://frozenfox.freehostia.com/cappy/) (just get getlibs-all.deb and install)  Getlibs is a wonderful tool that takes care of all the missing 32 bit libs automatically.
* enter in a terminal: sudo getlibs -i lexmark-inkjet-08-driver-1.0-1.i386.deb
* now your Lexmark should do its job ...

---

### Post by satish.bhawra.88 on 2009-09-03
safety concern is the most need ful of the lot

---

### Post by afrodeity on 2009-09-04
> **Magic_Spehar said:**
> I found the solution for the missing 64 bit linux driver of my Lexmark X2650. I guess there will be an similar solution for all people with a Lexmark X-series printer and a 64-bit Ubuntu system.  
You need a part of the code that Nathan726 used in this thread (thanks for that, by the way...) 

Now, here's the complete solution
---------------------------------
* download lexmark-inkjet-08-driver-1.0-1.i386.deb.sh.zip for Ubuntu 32 bit from the Lexmark website
* unzip 'lexmark-inkjet-08-driver-1.0-1.i386.deb.sh.zip'
* enter in a terminal:  sudo ./lexmark-inkjet-08-driver-1.0-1.i386.deb.sh --noexec --target lexmark_install
* Now go to your directory lexmark_install
* In that directory you'll find a file named arch.tar   Unzip that file.
* Once unzipped you'll find lexmark-inkjet-08-driver-1.0-1.i386.deb
* Ok, now download and install the program getlibs from [http://frozenfox.freehostia.com/cappy/](http://frozenfox.freehostia.com/cappy/) (just get getlibs-all.deb and install)  Getlibs is a wonderful tool that takes care of all the missing 32 bit libs automatically.
* enter in a terminal: sudo getlibs -i lexmark-inkjet-08-driver-1.0-1.i386.deb
* now your Lexmark should do its job ...

Doing this installed some libraries but what then? Sorry to be a complete nonse, but I also tried the original installer which still doesn't install.

```
 sudo getlibs -i lexmark-inkjet-08-driver-1.0-1.i386.deb
[sudo] password for afrodeity: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ia32-libs is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.
Installing libraries ...

```

---

### Post by nathan726 on 2009-09-04
> **Magic_Spehar said:**
> 
* Now go to your directory lexmark_install
* In that directory you'll find a file named arch.tar   Unzip that file.
* Once unzipped you'll find lexmark-inkjet-08-driver-1.0-1.i386.deb


Oddly, in my lexmark_install directory I don't have a "arch.tar" file, instead it's called "instarchive_all" - I managed to open it after I appended a ".lzma" extension to the file name. It contains 7 files, including the 10.3Mb lexmark-inkjet-08-driver-1.0-1.i386.deb package.

---

### Post by Magic_Spehar on 2009-09-04
> **afrodeity said:**
> Doing this installed some libraries but what then? Sorry to be a complete nonse, but I also tried the original installer which still doesn't install.



Normally that should be it.  You shouldn't need the orginal installer script.

Check to see if your printer is installed now by going to system - administration - printing.  If it's not, try going to Server - New - Printer then the system should look automatically and you may find a Lexmark 2600 connected to usb.

---

### Post by Magic_Spehar on 2009-09-06
There's also another solution for those with a 64 bit Ubuntu 9.04 system  who want to use their Lexmark X Series printer.  You can create a chrooted 32 bit environment. The solution below also works with my Lexmark 3-in-1 X2650 printer and I also can use my scanner without any problem with xsane. 

Step 1:

    * sudo apt-get install dchroot debootstrap
    * sudo mkdir /chroot/
    * sudo gedit /etc/dchroot.conf
          o Add this line: jaunty /chroot
    * sudo debootstrap --arch i386 jaunty /chroot/ [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)
    * sudo chroot /chroot/
    * dpkg-reconfigure locales

Step 2:
In another terminal window (or by existing chroot):

    * sudo gedit /chroot/etc/apt/sources.list
    * Add the following lines:
          o deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jaunty main restricted universe multiverse
          o deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted universe multiverse

(We do this step because gedit has yet to be installed in the chroot environment)

Step 3:
In your chrooted environment (chroot /chroot):

    * apt-get update ; apt-get upgrade

Step 4:
In another terminal window (or by existing chroot):

    * sudo cp /etc/passwd /chroot/etc/
    * sudo cp /etc/shadow /chroot/etc/
    * sudo cp /etc/group /chroot/etc/
    * sudo cp /etc/sudoers /chroot/etc/
    * sudo cp /etc/hosts /chroot/etc/
    * sudo gedit /etc/fstab
    * Add the following lines:
          o /home /chroot/home none bind 0 0
          o /tmp /chroot/tmp none bind 0 0
          o /dev /chroot/dev none bind 0 0
          o /proc /chroot/proc proc defaults 0 0
          o /media/cdrom0 /chroot/media/cdrom0 none bind 0 0
          o /usr/share/fonts /chroot/usr/share/fonts none bind 0 0
          o devpts /chroot/dev/pts devpts rw,noexec,nosuid,gid=5,mode=620 0 0
    * sudo mkdir /chroot/media/cdrom0
    * sudo mount -a
    * sudo gedit /usr/local/bin/do_dchroot
    * Add the following:
          o #!/bin/sh
          o /usr/bin/dchroot -d "`echo $0 | sed 's|^.*/||'` $*"
    * sudo chmod 755 /usr/local/bin/do_dchroot

Step 5:
In a new terminal:

    * dchroot -d
    * sudo apt-get install synaptic
    * sudo ln -s /usr/sbin/synaptic /usr/sbin/synaptic32
    * exit
    * sudo ln -s /usr/local/bin/do_dchroot /usr/local/bin/synaptic32
    * sudo synaptic32

Now you can install all the programs in 32 bit you want.  In my case I installed Openoffice, Firefox and Xsane. 

Normally you should be able to install the installation script for your Lexmark printer driver without any problem. 
Enter a terminal.  Then use the following commands:
    * sudo linux32 chroot /chroot
    * go to the directory where you have your downloaded Lexmark installation script.
    * ./yourscript.deb.sh

Now if want for to print a document in open office. Go to a terminal and enter * dchroot -d
      * ooffice

If you want to scan a document, go to terminal and enter
      * dchroot -d
      * xsane

If you want to be able to easily launch 32 bit chroot apps directly from your 64 bit environment symlink the app name to /usr/local/bin/do_dchroot. If you're using this as desktop system you'll probably want to use synaptic to install x, gnome, ubuntu specific themes, etc.

---

### Post by goehle on 2009-09-27
Couple of comments.  This chroot works great for me, but I had to do a couple of things first. Before you run dpkg-reconfigure locales run this

* sudo cp /var/lib/locales/supported.d/* /chroot/var/lib/locales/supported.d/

This makes the dpkg-reconfigure work properly.  Next, before you install your printer install CUPS in the chrooted environment

* dchroot -d 
* sudo apt-get install cups

At least I needed to do those things before it worked.

---

### Post by goehle on 2009-09-28
A couple of further things to add as I work everything out. 


3.  You may find your printer disappearing after reboot.  This is because the 32 bit version of CUPS doesn't automatically get started.  In order for this to happen you should do the following

* sudo gedit /etc/init.d/cups32
Add the following lines
o #!/bin/sh
o dchroot -d /etc/init.d/cups $1
Run the command
* update-rc.d /etc/init.d/cups32 defaults

4. You may find that xsane doesn't work unless you run it as root.  In order to fix this you should run the command

* sudo cp /chroot/usr/local/lexmark/lxk08/etc/99-lexmark-2600-series.rules /etc/udev/rules.d/

After a restart this will cause udev to apply the proper permissions to your printer/scanner and will allow you to use xsane as a normal user.

---

### Post by its_jon on 2009-09-30
I checked out the files i am supposed to have in lexmark_install folder under nautilus as root.... I renamed the files so they opened in archive manager but ony one file inside.... not 7 ?

and the info under that appears to be relevant to 64 bit ubuntu, this one is 32.

as karmic is nearly here, is it wise for me to wait and see if the cups is upgraded then ?

thanks
Jon
Scotland

---

### Post by nathan726 on 2009-09-30
You don't need to rename any files for the 32 bit install. You don't need to do anything as root. There is no problem with cups - the problem is with one of Lexmark's installer scripts. They made an error that you need to fix to get this working.

I explained what you need to on the first page: [http://ubuntuforums.org/showpost.php?p=7713382&postcount=2](http://ubuntuforums.org/showpost.php?p=7713382&postcount=2)

---

### Post by its_jon on 2009-10-01
Just open it in a text editor and add '--[[' and '--]]' like this:

??????

I checked your post... looked at the code you posted which appeared to be exactly the same as the code at the bottom of the file....so at least I am looking in the right place.

at first I cut and paste the your code over the top incase I missed anything... then I tried editing anything that said false to true within that section of code.

unless I have to put 

'--[[' and '--]]'

somewhere ?

thanks for your patience....

regards
John

---

### Post by nathan726 on 2009-10-01
You just need to type --[[ and --]] at the exact places I put them as shown in the following example in red...

Before:
```
function is_cups_version_ok()
    local bRet = true
    local packager = get_system_packaging()
    local tmp_path = g_mysecurepath
    local busehome = false
```After:
```
function is_cups_version_ok()
    local bRet = true
    [COLOR=Red]**--[[**[/COLOR]local packager = get_system_packaging()
    local tmp_path = g_mysecurepath
    local busehome = false
```Before:
```
    if busehome == true then
        -- os.remove(tmp_path .. '/cups_packages_072006')
    end
    
    return bRet
end
```After:
```
    if busehome == true then
        -- os.remove(tmp_path .. '/cups_packages_072006')
    end
    [COLOR=Red]**--]]**[/COLOR]
    return bRet
end
```Then save and close the file.

  Now that the file is fixed, you need to open the terminal and type the following (replace 'home/nathan/downloads/lexmark_install' with the location of the lexmark_install folder on your pc):

```
cd '/home/nathan/downloads/lexmark_install'
sudo ./startupinstaller.sh
```

---

### Post by cgarre on 2009-11-29
I have an X2600 Lexmark and I installed the driver from Lexmark website and thats it .. there was no problem, scanning and printing works. Just make sure you restart after the install. 

I have ubuntu 9.10 and i did not explicitly install anything else.

---

### Post by nathan726 on 2009-11-30
> **cgarre said:**
> I installed the driver from Lexmark website and thats it .. there was no problem.

Lexmark must have fixed the bug in the install script =D>

Edit: or maybe they haven't, if the next post is anything to go by...

---

### Post by janev on 2009-11-30
> **its_jon said:**
> I recently installed Ubuntu 9.4 on a laptop.... sorted out the wireless chip, thought everything was ok....
however the Lexmark printer is not working...

I have followed these instructions which appear to be full of hope:-
[http://forums.linux-foundation.org/read.php?29,9780,9780](http://forums.linux-foundation.org/read.php?29,9780,9780)

When I run the installer I get the error 

```
The installer has detected the operating system does not meet CUPS minimum version requirements. Please install CUPS version 1.2 or higher and run the installer again.
```I checked in synaptic and found (or assume) to be running a higher version of Cups
Cups 1,3,9-17 ?????

Help please
John in 
Scotland
I am unable to download missing cups for Lexmark X2650 Please help

---

### Post by nathan726 on 2009-12-01
Read what is already written... everything you need to do is already explained earlier in this thread... i can't make it much simpler.

You **do not** need to update cups. Cups is fine.
The actual problem is the script that Lexmark use to check your cups version... it doesn't work correctly.
Here is a summary of what you need to do to fix the cups error...

* First (if you haven't done so already) you need to unzip the .zip file, which will give you a .sh file

* Dump the contents of that .sh file to the "lexmark_install" folder

* Modify the /lexmark_install/config/run.lua file

* Run the startupinstaller.sh file as root

Read my earlier posts for more details on how to do the above steps.
And then if you are still stuck, explain your problem and I will try to help.

---

### Post by XGC Sentinel XS on 2009-12-01
> **nathan726 said:**
> Read what is already written... everything you need to do is already explained earlier in this thread... i can't make it much simpler.

I followed all of the directions from your first post and everything went well until I got to this part:
 
"* Run the startupinstaller.sh file as root"

But when I try to run sudo ./startupinstaller.sh, I get this Error message:
"Lua error detected: While parsing install.lua: install.lua:118: Overflow detected: Not enough space for widget."

thoughts on this ??

---

### Post by nathan726 on 2009-12-01
Hmm... odd. I've got no idea why you'd get that error (and Google isn't any help either) :/

This probably won't work, but you could give it a try:
Copy your lexmark_install directory to the /tmp folder and then...
```
cd /tmp/lemark_install
sudo ./startupinstaller.sh
```If that fails, you might be able to install the driver manually... I'm not sure...
I'd need to do some experiments when I get some spare time.

---

### Post by afrodeity on 2009-12-02
I upgraded to Karmic x86 and all my troubles went away. No more 64bit Hell for me.

---

### Post by XGC Sentinel XS on 2009-12-05
> **nathan726 said:**
> Hmm... odd. I've got no idea why you'd get that error (and Google isn't any help either) :/

This probably won't work, but you could give it a try:
Copy your lexmark_install directory to the /tmp folder and then...
```
cd /tmp/lemark_install
sudo ./startupinstaller.sh
```If that fails, you might be able to install the driver manually... I'm not sure...
I'd need to do some experiments when I get some spare time.


I tried that and got he same error message ..... kind of stuck .. thinking of going out to just buy a new printer, but I hate being beaten by a computer !! hahaha :p

---

### Post by nathan726 on 2009-12-06
You're not beaten yet, I've found a solution that should work.
Instead of relying on Lexmark's installation scripts, you can install the driver directly...

Change directory to location of the Lexmark driver you downloaded, eg:
```
cd /tmp
```Extract the .zip file:
```
unzip 'lexmark-inkjet-08-driver-1.0-1.i386.deb.sh.zip'
```Dump the contents of the .sh file:
```
./lexmark-inkjet-08-driver-1.0-1.i386.deb.sh --noexec --target lexmark_install
```Change directory to lexmark_install:
```
cd lexmark_install
```Extract the "instarchive_all" file (which is actually a "tar.lzma" file without the extension):
```
tar -xvvf instarchive_all --lzma
```And finally you can install the driver directly from the deb package:
```
sudo dpkg --install lexmark-inkjet-08-driver-1.0-1.i386.deb
```Plug in your printer and it should work for printing and scanning (sudo simple-scan).

---

### Post by slonepaul on 2010-02-25
would you have anything for A Lexmark Interpret S405 on Karmic?? or even on Jaunty Ultimate Edition?

---

### Post by joshklewis on 2010-05-05
And finally you can install the driver from the deb package:

nathan, when I try to do that, I get an error. It says:

Error: Wrong architecture 'i386'

I am going to assume this is because I am using the 64 bit system? Or is it because I am using 10.04 instead of the version talked about in the post?

---

### Post by nathan726 on 2010-05-06
Hi Josh, to install a 32-bit package on a 64-bit system you can use the "--force-architecture" switch:
```
sudo dpkg -i --force-architecture lexmark-inkjet-08-driver-1.0-1.i386.deb
```

You'll probably need to install some 32 bit libraries on your system, check out:
[http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

---

### Post by joshklewis on 2010-05-09
I am a bit confused. I apologize for not catching on right away. I have done everything in your first post to change the coding in the is_cups_version_ok function.

I also installed getlib.

What do I need to do now in order to install the drivers for the printer?

Do I run the code you put in your previous post or do I run the startupinstaller.sh in the post on the first page?

---

### Post by nathan726 on 2010-05-10
Go to your lexmark_install and find the "instarchive_all" file. Rename this file to "instarchive_all.tar.lzma", right click it and select extract.
Inside instarchive_all/ you should find the lexmark-inkjet-08-driver-1.0-1.i386.deb file.

I'm not sure about the next step - but give it a try and let me know what happens:```

cd /path/to/lexmark_install/instarchive_all/
sudo getlibs -i lexmark-inkjet-08-driver-1.0-1.i386.deb
```

---

### Post by joshklewis on 2010-05-10
This is what happened when I typed in the code. Forgive me if I pasted into this post wrong. I can't remember how to format code on the forum.

```

joshua@joshua-laptop:~/Documents/Lexmark/lexmark_install/instarchive_all$ sudo getlibs -i lexmark-inkjet-08-driver-1.0-1.i386.deb
[sudo] password for joshua: 
Installing libraries ...
joshua@joshua-laptop:~/Documents/Lexmark/lexmark_install/instarchive_all$ 

```

---

### Post by joshklewis on 2010-05-10
I ran this:

```

sudo dpkg -i --force-architecture lexmark-inkjet-08-driver-1.0-1.i386.deb

```

and this is what I got:

```

joshua@joshua-laptop:~/Documents/Lexmark/lexmark_install/instarchive_all$ sudo dpkg -i --force-architecture lexmark-inkjet-08-driver-1.0-1.i386.deb
[sudo] password for joshua: 
dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
Selecting previously deselected package lexmark-inkjet-08-driver.
(Reading database ... 207621 files and directories currently installed.)
Unpacking lexmark-inkjet-08-driver (from lexmark-inkjet-08-driver-1.0-1.i386.deb) ...

--------------------------
Installing inkjet-08-driver ...
--------------------------
Setting up lexmark-inkjet-08-driver (1.0-1) ...
   -- Updating symbolic links
   -- Setting CUPS AppArmor profile to complain mode



Installation Complete.
--------------------------------------------

Please remember to review the license agreement (license.txt)
at /usr/lexinkjet/lxk08/docs/ before using this software.


joshua@joshua-laptop:~/Documents/Lexmark/lexmark_install/instarchive_all$

```

---

### Post by joshklewis on 2010-05-10
It is still not doing anything when I plug the printer in and try to print something. What should I try next?

---

### Post by nathan726 on 2010-05-10
Go to system >  administration > printing. If you can't see your printer, in the Server menu, select New > Printer.
Your system should detect the printer.

If that fails, then you could try what Magic_Spehar suggested in [post #13]("http://ubuntuforums.org/showthread.php?t=1223710&page=2#13").

---

### Post by joshklewis on 2010-05-10
It shows the printer in the printers list, but it does nothing when I plug the printer in and try to print something.

---

### Post by joshklewis on 2010-05-10
I just tried deleting the printer from the printing tool in administrator and start over by adding it again. It detected the printer and added it to the printing tool, but when I tried to print a test page, I got an error.
The error says "Printing Error. There was a problem processing document 'Test Page'" It gives me an option to diagnose the problem. By diagnosing the problem, I get a print troubleshooting window where it wants me to choose the printer (my printer is listed). I choose my printer and it says:

"There are status messages associated with this queue.
The printer's state message is: 'usr/local/lexmark/lxko8/bin/printdriver failed"

I'm not sure what to do to get it to recognize the driver.

---

### Post by nathan726 on 2010-05-11
Okay... try this:
```
sudo getlibs /usr/local/lexmark/lxk08/bin/printdriver
sudo getlibs /usr/local/lexmark/lxk08/bin/prnutility
sudo getlibs /usr/local/lexmark/lxk08/bin/lxkusb
sudo getlibs /usr/local/lexmark/lxk08/bin/printdriver
sudo getlibs /usr/local/lexmark/lxk08/lib/liblxdphpec.so
sudo getlibs /usr/local/lexmark/lxk08/lib/libsane-Lexmarklxdn.so.1.0.18
sudo getlibs /usr/local/lexmark/lxk08/lib/liblxdnhpeh.so
sudo getlibs /usr/local/lexmark/lxk08/lib/liblxdphpeh.so
sudo getlibs /usr/local/lexmark/lxk08/lib/liblxdnhpep.so
sudo getlibs /usr/local/lexmark/lxk08/lib/libnpa407.so
sudo getlibs /usr/local/lexmark/lxk08/lib/libprinterdictionary.so
sudo getlibs /usr/local/lexmark/lxk08/lib/liblxdnhpec.so
sudo getlibs /usr/local/lexmark/lxk08/lib/libusblp.so
sudo getlibs /usr/local/lexmark/lxk08/lib/liblxdnflib.so
sudo getlibs /usr/local/lexmark/lxk08/lib/liblxdphpep.so
sudo getlibs /usr/local/lexmark/lxk08/lib/libuiocmd.so
sudo getlibs /usr/local/lexmark/lxk08/lib/libhdctransport.so
sudo getlibs /usr/local/lexmark/lxk08/lib/libprintengine.so
sudo getlibs /usr/local/lexmark/lxk08/lib/libuiocli.so
sudo getlibs /usr/local/lexmark/lxk08/lib/libCS_ScanCorrect.so
sudo getlibs /usr/local/lexmark/lxk08/lib/liblxdpflib.so
sudo getlibs /usr/local/lexmark/lxk08/lib/liblxkscan.so

```

---

### Post by joshklewis on 2010-05-11
Here is the result that I got from running those.
```

joshua@joshua-laptop:~$ sudo getlibs /usr/local/lexmark/lxk08/bin/printdriver
[sudo] password for joshua: 
This application isn't missing any dependencies
joshua@joshua-laptop:~$ sudo getlibs /usr/local/lexmark/lxk08/bin/prnutility
This application isn't missing any dependencies
joshua@joshua-laptop:~$ sudo getlibs /usr/local/lexmark/lxk08/bin/lxkusb
This application isn't missing any dependencies
joshua@joshua-laptop:~$ sudo getlibs /usr/local/lexmark/lxk08/bin/printdriver
This application isn't missing any dependencies
joshua@joshua-laptop:~$ sudo getlibs /usr/local/lexmark/lxk08/lib/liblxdphpec.so 
No match for liblxdphpec.so
No packages to install
joshua@joshua-laptop:~$ 
joshua@joshua-laptop:~$ sudo getlibs /usr/local/lexmark/lxk08/lib/libsane-Lexmarklxdn.so.1.0.18
No match for libsane-Lexmarklxdn.so.1.0.18
No packages to install
joshua@joshua-laptop:~$ sudo getlibs /usr/local/lexmark/lxk08/lib/liblxdnhpeh.soNo match for liblxdnhpeh.so
No packages to install
joshua@joshua-laptop:~$ sudo getlibs /usr/local/lexmark/lxk08/lib/liblxdphpeh.soNo match for liblxdphpeh.so
No packages to install
joshua@joshua-laptop:~$ sudo getlibs /usr/local/lexmark/lxk08/lib/libnpa407.so
No match for libnpa407.so
No packages to install
joshua@joshua-laptop:~$ sudo getlibs /usr/local/lexmark/lxk08/lib/libprinterdictionary.so
No match for libprinterdictionary.so
No packages to install
joshua@joshua-laptop:~$ sudo getlibs /usr/local/lexmark/lxk08/lib/liblxdnhpec.soNo match for liblxdnhpec.so
No packages to install
joshua@joshua-laptop:~$ sudo getlibs /usr/local/lexmark/lxk08/lib/libusblp.so
No match for libusblp.so
No packages to install
joshua@joshua-laptop:~$ sudo getlibs /usr/local/lexmark/lxk08/lib/liblxdnflib.soNo match for liblxdnflib.so
No packages to install
joshua@joshua-laptop:~$ sudo getlibs /usr/local/lexmark/lxk08/lib/liblxdphpep.soNo match for liblxdphpep.so
No packages to install
joshua@joshua-laptop:~$ sudo getlibs /usr/local/lexmark/lxk08/lib/libuiocmd.so
No match for libuiocmd.so
No packages to install
joshua@joshua-laptop:~$ sudo getlibs /usr/local/lexmark/lxk08/lib/libhdctransport.so
No match for libhdctransport.so
No packages to install
joshua@joshua-laptop:~$ sudo getlibs /usr/local/lexmark/lxk08/lib/libprintengine.so
No match for libprintengine.so
No packages to install
joshua@joshua-laptop:~$ sudo getlibs /usr/local/lexmark/lxk08/lib/libuiocli.so
No match for libuiocli.so
No packages to install
joshua@joshua-laptop:~$ sudo getlibs /usr/local/lexmark/lxk08/lib/libCS_ScanCorrect.so
No match for libCS_ScanCorrect.so
No packages to install
joshua@joshua-laptop:~$ sudo getlibs /usr/local/lexmark/lxk08/lib/liblxdpflib.soNo match for liblxdpflib.so
No packages to install
joshua@joshua-laptop:~$ sudo getlibs /usr/local/lexmark/lxk08/lib/liblxkscan.so
No match for liblxkscan.so
No packages to install
joshua@joshua-laptop:~$ 


```

---

### Post by nathan726 on 2010-05-11
Can you run this and post the output:
```
/usr/local/lexmark/lxk08/bin/printdriver
```

---

### Post by joshklewis on 2010-05-12
```

joshua@joshua-laptop:~$ /usr/local/lexmark/lxk08/bin/printdriver
Usage: /usr/local/lexmark/lxk08/bin/printdriver job-id user title copies options [file]
joshua@joshua-laptop:~$ 

```

---

### Post by nathan726 on 2010-05-12
For some reason the driver is failing and I can't pinpoint the source of the problem ](*,)

Maybe it would be easier if you installed the x86 32-bit version of 10.04 instead.
You won't have the advantages of 64-bit, but it is easier to get things working in 32-bit Ubuntu.

---

### Post by joshklewis on 2010-05-13
Yeah, I had actually considered that, but that means I'd have to download it all over again. I have a slow connection, it took me 6.5 hours to download this one. I may just have to buy a linux friendly printer.

---

### Post by afrodeity on 2011-06-06
Trying to reinstall the damn driver after the natty upgrade. Here is what happens:

```

sudo ./startupinstaller.sh 
Collecting info for this system...
Operating system: linux
CPU Arch: x86
./startupinstaller.sh: 169: /home/afrodeity/Software/Lexmark: Permission denied
./startupinstaller.sh: 169: /home/afrodeity/Software/Lexmark: Permission denied
./startupinstaller.sh: 169: /home/afrodeity/Software/Lexmark: Permission denied
Error: Couldn't find any suitable frontend for your system
```

```


sudo sh startupinstaller.sh 
Collecting info for this system...
Operating system: linux
CPU Arch: x86
startupinstaller.sh: 169: /home/afrodeity/Software/Lexmark: Permission denied
startupinstaller.sh: 169: /home/afrodeity/Software/Lexmark: Permission denied
startupinstaller.sh: 169: /home/afrodeity/Software/Lexmark: Permission denied
Unsupported patch version!
chmod: cannot access `bin/linux/x86/libc.so.6/libstdc++.so.5/gtk': No such file or directory
ldd: bin/linux/x86/libc.so.6/libstdc++.so.5/gtk: No such file or directory
startupinstaller.sh: 169: /home/afrodeity/Software/Lexmark: Permission denied
Unsupported patch version!
chmod: cannot access `bin/linux/x86/libc.so.6/libstdc++.so.5/fltk': No such file or directory
ldd: bin/linux/x86/libc.so.6/libstdc++.so.5/fltk: No such file or directory
startupinstaller.sh: 169: /home/afrodeity/Software/Lexmark: Permission denied
Unsupported patch version!
chmod: cannot access `bin/linux/x86/libc.so.6/libstdc++.so.5/ncurs': No such file or directory****
ldd: bin/linux/x86/libc.so.6/libstdc++.so.5/ncurs: No such file or directory
startupinstaller.sh: 169: /home/afrodeity/Software/Lexmark: Permission denied
Error: Couldn't find any suitable frontend for your system

```

---

### Post by nathan726 on 2011-07-25
Hi afrodeity, have you had any luck installing the driver directly from the .deb (as explained in [post 28]("http://ubuntuforums.org/showpost.php?p=8454063&postcount=28")). It's working perfectly for me on 32 bit Natty.

---

### Post by afrodeity on 2011-07-28
> **nathan726 said:**
> Hi afrodeity, have you had any luck installing the driver directly from the .deb (as explained in [post 28]("http://ubuntuforums.org/showpost.php?p=8454063&postcount=28")). It's working perfectly for me on 32 bit Natty.

Why, yes, posting 28 is the solution, thanks. I also had to replace the nonrefillable cartridge, now the thing is having problems loading paper, I won't be buying Lexmark products ever again.

---

### Post by aaronofruston on 2011-10-12
Lexmark sucks printer goes in trash tonight. I am running Natty 64 and tried all the fixes in this forum. Still nothing. So I will be looking for a new printer on other forums that actually works on ubuntu.

---

### Post by GTrip on 2011-10-25
I agree with the trash can.  I have the x2600 series printer too and gave up on the 64bit version.  Lexmark is no help and assures the 32bit driver to work.  I have great confidence since their support staff hardly knows what the word "Linux" means.

My solution was that I also have a Fedora 32bit machine working.  The printer/scanner functions work great on a 32bit platform(operated from that machine, NOT shared).  Other than that, I also have an HP printer that does a great job and is fully supported 32 OR 64 bit.  It shares easily over the network to any other computer too.

HP, with their great Linux support, is the way to go in my opinion.

---

