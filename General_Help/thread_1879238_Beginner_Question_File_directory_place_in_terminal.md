---
title: "Beginner Question: File directory place in terminal"
date: 2011-11-11
forum: General Help
---

### Post by emptycoder on 2011-11-11
Hi, I was following a tutorial of installing a graphic driver, everything was working fine until this step:
In terminal: cd /file_dictory
my file named ATI and it's on desktop, I checked out the proprieties to make sure of it's location and it was like this /home/MyUsername/desktop/ATI
So I entered it like this: cd /home/MyUsername/desktop/ATI
But it says directory can not be found
Am I doing something wrong? please help me.
Thanks.

---

### Post by nothingspecial on 2011-11-11
Desktop with a capital D

linux is case sensetive. :)

---

### Post by emptycoder on 2011-11-11
Thanks, but I got another problem.

Here's the tutorial:

Once downloaded go to the file location and set it to run as executable

cd /path_of_the_file
chmod 755 ati-driver-installer-11-10-x86.x86_64.run

____________________________________________________

I entered my file location (Which contains ATI driver)
cd /home/username/Desktop/ATI

And I got this:
username@ubuntu:~/ATI$

And simply nothing happened, I tried to enter the second line but I got the same thing

username@ubuntu:~/ATI$ chmod 755 ati-driver-installer-11-10-x86.x86_64.run
username@ubuntu:~/ATI$

Sorry, I'm still new to Linux, so could you please tell me what's wrong?

---

### Post by matt_symes on 2011-11-11
Hi

You need to run the installer.

You do that by typing

```
./ati-driver-installer-11-10-x86.x86_64.run
```

or 
```

sudo ./ati-driver-installer-11-10-x86.x86_64.run
```

The correct command depends on the installer.

Can you post a link to the tutorial you are following then we can help you out.

Kind regards

---

### Post by nothingspecial on 2011-11-11
> **emptycoder said:**
> Thanks, but I got another problem.

Here's the tutorial:

Once downloaded go to the file location and set it to run as executable

cd /path_of_the_file
chmod 755 ati-driver-installer-11-10-x86.x86_64.run

____________________________________________________

I entered my file location (Which contains ATI driver)
cd /home/username/Desktop/ATI

And I got this:
username@ubuntu:~/ATI$


And simply nothing happened, 



That's because it worked, you are now in the ATI folder. :)

> **emptycoder said:**
> I tried to enter the second line but I got the same thing

username@ubuntu:~/ATI$ chmod 755 ati-driver-installer-11-10-x86.x86_64.run
username@ubuntu:~/ATI$

Sorry, I'm still new to Linux, so could you please tell me what's wrong?

Again, that's because it worked, you changed the permissions of the file :)

Linux doesn't usually tell you if you did it right but it will give errors if you do it wrong.

But like matt_symes said, post a link to the tutorial.

---

### Post by emptycoder on 2011-11-11
Here's the link:

[http://www.uptechtalk.com/?p=86](http://www.uptechtalk.com/?p=86)

---

### Post by matt_symes on 2011-11-11
Hi
> 
*For 32 bit Ubuntu use this step to install*
 sh ./ati-driver-installer-11-5-x86.x86_64.run
 *For 64 bit you need to run these steps*
 sh ./ati-driver-installer-11-10-x86.x86_64.run --buildpkg Ubuntu/natty
or
sh ./ati-driver-installer-11-10-x86.x86_64.run --buildpkg Ubuntu/oneiric
*(depending on your Ubuntu version)*
sudo dpkg -i fglrx*.deb
 Once the driver is installed you need to start up a new xorg.conf file with this command
  sudo aticonfig --initial -f
 Reboot
We need to know if you are running 32-bit or 64-bit Ubuntu.

Open a terminal and type

```
uname -a
```

```
cat /etc/lsb-release
```

Post the results back here.

Kind regards

---

### Post by emptycoder on 2011-11-11
Sorry, I forgot to tell the details.
I'm using Ubuntu 11.10 64bit
So far I haven't installed anything except Gnome 3 shell. and about the tutorials, here what I have done so far:

Step 1: 
Remove the fglrx drivers if you installed them


I skipped this one because I didn't install any fglrx (Because it's not compatible with Gnome 3 yet)


Step 2:
or if you installed the ATI driver package from ATI’s site without building packages for your system


I skipped that too because I tried it before, running ATI .run file in terminal and installing it in that way made my computer slow, I had to make a new clean install of ubuntu because I didn't know how to remove ATI Driver.


Step 3:
Download the newest ATI driver (current version is 11.10)


I have done that but not with Terminal command, I did with a Download Manager because it's much faster.


Step 4:
**If you have a 64 bit system, then install this before anything**


**I have installed **ia32-libs because my system is 64 bit


step 5:
Once downloaded go to the file location and set it to run as executable


And that's the step where I found myself stuck.


I believe after that step there will be only two steps left


*For 64 bit you need to run these steps*


Once the driver is installed you need to start up a new xorg.conf file with this command


Then reboot.

---

### Post by matt_symes on 2011-11-11
Hi

You need to run this command (run in a bourne shell but may also work in bash)

```
sh ./ati-driver-installer-11-10-x86.x86_64.run --buildpkg Ubuntu/oneiric
```Then this one

```
sudo dpkg -i fglrx*.deb
```and finally this one.

  ```
sudo aticonfig --initial -f
```

Kind regards

---

### Post by brunopereira81 on 2011-11-11
@emptycoder

You can see if the file became executable using the command ```
ls -l
```If the command returns file not found then you are pointing it to a non existent file, make sure that you are using the correct file name on the file path

 ```
chmod 755 <filename>
``` does not give an output unless its a fault.

Follow the instructions using a terminal so there are no confusions, the download might be faster with a download manager but it sure saves you this kind of pain.

Regards

---

### Post by emptycoder on 2011-11-11
I will try this later,unfortunately my connection being slow, I will update this thread later and I hope I will update it to SOLVED.
Thanks a lot everyone for your help.

---

### Post by brunopereira81 on 2011-11-11
Np, you can also drop a comment on the site and I will try to help you out with anything else.

Gl

---

### Post by emptycoder on 2011-11-12
[FONT=Arial]Hello again, sorry if I took so long but my Internet connection was really slow, sorry again.
Anyway, I'm stuck on the last step.

This command worked fine with no errors at all:
sh ./ati-driver-installer-11-10-x86.x86_64.run --buildpkg Ubuntu/oneiric

but the last one didn't work well, it contains a lot of errors:
sudo dpkg -i fglrx*.deb

Here's the terminal log:

(Reading database ... 137974 files and directories currently installed.)
Preparing to replace fglrx 2:8.902-0ubuntu1 (using fglrx_8.902-0ubuntu1_amd64.deb) ...
Unpacking replacement fglrx ...
Preparing to replace fglrx-amdcccle 2:8.902-0ubuntu1 (using fglrx-amdcccle_8.902-0ubuntu1_amd64.deb) ...
Unpacking replacement fglrx-amdcccle ...
Preparing to replace fglrx-dev 2:8.902-0ubuntu1 (using fglrx-dev_8.902-0ubuntu1_amd64.deb) ...
Unpacking replacement fglrx-dev ...
dpkg: dependency problems prevent configuration of fglrx:
 fglrx depends on dkms; however:
  Package dkms is not installed.
dpkg: error processing fglrx (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of fglrx-amdcccle:
 fglrx-amdcccle depends on fglrx; however:
  Package fglrx is not configured yet.
dpkg: error processing fglrx-amdcccle (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of fglrx-dev:
 fglrx-dev depends on fglrx; however:
  Package fglrx is not configured yet.
dpkg: error processing fglrx-dev (--install):
 dependency problems - leaving unconfigured
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Errors were encountered while processing:
 fglrx
 fglrx-amdcccle
 fglrx-dev


I have checked out the graphic card and it's still the same driver that comes with ubuntu as defualt (Gallium 0.4 on AMD CEDAR )

Please help me!
[/FONT]

---

### Post by matt_symes on 2011-11-14
Hi
> 
[FONT=Arial]fglrx depends on dkms; however:
  Package dkms is not installed.[/FONT]I'm surprised it's not installed though.

```
sudo apt-get install dkms
```

Then install the deb file again.

Kind regards

---

