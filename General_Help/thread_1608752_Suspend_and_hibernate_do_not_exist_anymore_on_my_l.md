---
title: "Suspend and hibernate do not exist anymore on my laptop"
date: 2010-10-29
forum: General Help
---

### Post by gauravbutola on 2010-10-29
When I close the lid of my laptop and open it after some time I am greeted with a message "Failed to suspend". When I tried to manually suspend/hibernate, I saw these options are not available there at all. Of course, they did exist when I did the fresh installation but I cant see them anymore. I am totally pissed off with this. Please help.

[IMG]http://imgur.com/vuFhc.png[/IMG]

---

### Post by gauravbutola on 2010-10-30
Guys I seriously need to figure this out. Its annoying to shut down my laptop when I can suspend/hibernate.
As I said it did exist before, but for some reason I cant see it in the menu aymore. see the screenshot.

---

### Post by Verbeck on 2010-10-30
try pressing alt+ctrl+delete. does the box which pop up have a hibernate option?

---

### Post by matt_symes on 2010-10-30
Hi

Also try

Open a terminal. Type

sudo pm-suspend

and enter you password. Does this suspend?

Kind regards

---

### Post by gauravbutola on 2010-10-30
> **Verbeck said:**
> try pressing alt+ctrl+delete. does the box which pop up have a hibernate option?
Only shutdown and Restart options are there now :(

---

### Post by gauravbutola on 2010-10-30
> **matt_symes said:**
> Hi

Also try

Open a terminal. Type

sudo pm-suspend

and enter you password. Does this suspend?

Kind regards
Got error
sudo: pm-suspend: command not found

---

### Post by matt_symes on 2010-10-30
Hi 

Under System->Preferences do you have a power management option?

Kind regards

---

### Post by gauravbutola on 2010-10-30
> **matt_symes said:**
> Hi 

Under System->Preferences do you have a power management option?

Kind regards
yep I have the power management option but there doesn't seem to be any option for suspend/hibernate anymore.
what should I do now.

thanks for the reply

---

### Post by matt_symes on 2010-10-30
Hi 

Reboot your PC and select an older kernel from the grub menu. Boot into that and see if you have suspend and hibernate then. Then report back.

Kind regards

---

### Post by gauravbutola on 2010-10-30
> **matt_symes said:**
> Hi 

Reboot your PC and select an older kernel from the grub menu. Boot into that and see if you have suspend and hibernate then. Then report back.

Kind regards
My system is up to date but I think I removed the old kernels from Ubuntu Tweak :'(

Am I stuck now?

---

### Post by matt_symes on 2010-10-30
Hi

> My system is up to date but I think I removed the old kernels from Ubuntu Tweak :'(

Around the same  time you lost suspend?

Type this 

ls /usr/sbin | grep pm-suspend

Does it return anything?

Kind regards

---

### Post by gauravbutola on 2010-10-30
> **matt_symes said:**
> Hi



Around the same  time you lost suspend?

Type this 

ls /usr/sbin | grep pm-suspend

Does it return anything?

Kind regards
No, It doesn't return anything. No result, No Error.

---

### Post by matt_symes on 2010-10-30
Hi

Does 

ls /etc/acpi | grep sleep

return any results???

Kind regards

---

### Post by gauravbutola on 2010-10-30
Here is the output

gaurav@gaurav-HCL-ME-Laptop:~$ ls /etc/acpi | grep sleep
sleepbtn.sh
sleep.sh

---

### Post by matt_symes on 2010-10-30
Hi

Alright.

Type at the termianl

sudo /etc/acpi/sleepbtn.sh

Enter you password press return and press space. Does that suspend you machine?

Kind regards

---

### Post by gauravbutola on 2010-10-30
> **matt_symes said:**
> Hi

Alright.

Type at the termianl

sudo /etc/acpi/sleepbtn.sh

Enter you password press return and press space. Does that suspend you machine?

Kind regards
first of all thanks a lot for your constant replies :)

I ran the command sudo /etc/acpi/sleepbtn.sh
and entered my password but didn't get any error or any output.


gaurav@gaurav-HCL-ME-Laptop:~$ sudo /etc/acpi/sleepbtn.sh
[sudo] password for gaurav: 
gaurav@gaurav-HCL-ME-Laptop:~$

---

### Post by matt_symes on 2010-10-30
Hi

Unless someone else can continue, we will have to continue this tomorrow (as is 6.00PM in the evening in the UK on a Saturday night and there is beer to drink :)).

Kind regards

---

### Post by gauravbutola on 2010-10-30
fair enough ;)

in the mean time, hope someone else can come and sort this out for me.

---

### Post by Qselma on 2010-10-31
hello

My Suspend/Hibernate worked well out-of-the-box when i installed Ubuntu. But I somehow lost both options in the upper right menu the other day while messing with some battery stat tools. But I just managed to get it back working this way:

open the Software center and type 'acpi-support' in the search bar. Make sure, that the package is installed. Reboot, and voilà: suspend and hibernate are back and working again for me. maybe this will fix it for you, too.

Kind regards,
Qselma

---

### Post by gauravbutola on 2010-10-31
> **Qselma said:**
> hello

My Suspend/Hibernate worked well out-of-the-box when i installed Ubuntu. But I somehow lost both options in the upper right menu the other day while messing with some battery stat tools. But I just managed to get it back working this way:

open the Software center and type 'acpi-support' in the search bar. Make sure, that the package is installed. Reboot, and voilà: suspend and hibernate are back and working again for me. maybe this will fix it for you, too.

Kind regards,
Qselma
Thanks a lot Qselma. Really, this problem has really bugged me and now its all fine. thanks a ton.

---

### Post by tomek_wap on 2012-01-21
reinstalling "acpi-support" helps indeed. like I said reinstalling, as I always have it.

my notebook fails to suspend after updates. now it happened twice - 2nd after yesterdays update.

---

### Post by tomek_wap on 2012-01-23
yet another ubuntu updates today, and suspending stopped working again.
what's wrong with ubuntu ??

---

### Post by astrobob.tk on 2012-01-29
> **tomek_wap said:**
> yet another ubuntu updates today, and suspending stopped working again.
what's wrong with ubuntu ??

Indeed; I updated a while ago (~2 months) & the hibernation stopped working :S

I was reading the following thread: [http://ubuntuforums.org/showthread.php?p=11612569](http://ubuntuforums.org/showthread.php?p=11612569)

Maybe it helps you; I followed the link(in the thread): [http://turbulentsky.com/resume-from-hibernate-failed-on-ubuntu.html](http://turbulentsky.com/resume-from-hibernate-failed-on-ubuntu.html)

but I do not have enough time to continue. I will return to it after sometime.

Meanwhile, if you anything works for you, please update your thread.

regards

---

### Post by tomek_wap on 2012-01-29
since last time I've removed/uninstalled:  acpi-support  and it started working again :)

will see how it performs in next updates, and of not will go thru the links u've provided - thank you.

---

