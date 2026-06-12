---
title: "Updates fail"
date: 2012-06-17
forum: General Help
---

### Post by mountainman70 on 2012-06-17
Running Ubuntu 11.04. Can not get updates. This is the error I get. Can anyone tell me how to fix?

 Extracting templates from packages: 71%% Extracting templates from packages: 100%% 
Preconfiguring packages ... 
(Reading database ...  (Reading database ... 5%% (Reading database ... 10%% (Reading database ... 15%% (Reading database ... 20%% (Reading database ... 25%% (Reading database ... 30%% (Reading database ... 35%% (Reading database ... 40%% (Reading database ... 45%% (Reading database ... 50%% (Reading database ... 55%% (Reading database ... 60%% (Reading database ... 65%% (Reading database ... 70%% (Reading database ... 75%% (Reading database ... 80%% (Reading database ... 85%% (Reading database ... 90%% (Reading database ... 95%% (Reading database ... 100%% (Reading database ... 261567 files and directories currently installed.) 
Preparing to replace apt 0.8.13.2ubuntu4.4 (using .../apt_0.8.13.2ubuntu4.6_i386.deb) ... 
Unpacking replacement apt ... 
dpkg: ../../src/archives.c:968: tarobject: Assertion `r == stab.st_size' failed. 
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe) 
Processing triggers for man-db ... 

Thanks.

---

### Post by plucky on 2012-06-18
> **mountainman70 said:**
> Running Ubuntu 11.04. Can not get updates. This is the error I get. Can anyone tell me how to fix?

 Extracting templates from packages: 71%% Extracting templates from packages: 100%% 
Preconfiguring packages ... 
(Reading database ...  (Reading database ... 5%% (Reading database ... 10%% (Reading database ... 15%% (Reading database ... 20%% (Reading database ... 25%% (Reading database ... 30%% (Reading database ... 35%% (Reading database ... 40%% (Reading database ... 45%% (Reading database ... 50%% (Reading database ... 55%% (Reading database ... 60%% (Reading database ... 65%% (Reading database ... 70%% (Reading database ... 75%% (Reading database ... 80%% (Reading database ... 85%% (Reading database ... 90%% (Reading database ... 95%% (Reading database ... 100%% (Reading database ... 261567 files and directories currently installed.) 
Preparing to replace apt 0.8.13.2ubuntu4.4 (using .../apt_0.8.13.2ubuntu4.6_i386.deb) ... 
Unpacking replacement apt ... 
dpkg: ../../src/archives.c:968: tarobject: Assertion `r == stab.st_size' failed. 
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe) 
Processing triggers for man-db ... 

Thanks.

Open a terminal (CTRL+ALT+t) and use ```
sudo apt-get clean
sudo apt-get install -f
``` and post the output to the forum if there are any errors.

Use [noparse]```

```[/noparse] blocks to show the output.

Good luck

---

### Post by mountainman70 on 2012-06-18
> **plucky said:**
> Open a terminal (CTRL+ALT+t) and use ```
sudo apt-get clean
sudo apt-get install -f
``` and post the output to the forum if there are any errors.

Use [noparse]```

```[/noparse] blocks to show the output.

Good luck

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  apt
Suggested packages:
  apt-doc
Recommended packages:
  gpg
The following packages will be upgraded:
  apt
1 upgraded, 0 newly installed, 0 to remove and 12 not upgraded.
1 not fully installed or removed.
Need to get 2,104 kB of archives.
After this operation, 36.9 kB disk space will be freed.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates/main apt i386 0.8.13.2ubuntu4.6 [2,104 kB]
Fetched 2,104 kB in 15s (138 kB/s)                                             
(Reading database ... 260764 files and directories currently installed.)
Preparing to replace apt 0.8.13.2ubuntu4.4 (using .../apt_0.8.13.2ubuntu4.6_i386.deb) ...
Unpacking replacement apt ...
dpkg: ../../src/archives.c:968: tarobject: Assertion `r == stab.st_size' failed.
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
E: Sub-process /usr/bin/dpkg exited unexpectedly

---

### Post by plucky on 2012-06-18
As you are getting the same error,open Software Sources and change your server to the **Main Server** and try the same commands again.

If that works,don't forget to change the server back to your local server.

> dpkg: ../../src/archives.c:968: tarobject: Assertion `r == stab.st_size' failed.
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
E: Sub-process /usr/bin/dpkg exited unexpectedly 

It could also be a problem with dpkg which is used to install updates.

---

### Post by mountainman70 on 2012-06-18
> **plucky said:**
> As you are getting the same error,open Software Sources and change your server to the **Main Server** and try the same commands again.

If that works,don't forget to change the server back to your local server.



It could also be a problem with dpkg which is used to install updates.

Changed to Main Server and ran the commands and got same error. I am outside working and will check later to see if you have another step to try. Changed back to local server.

Thanks.

---

### Post by plucky on 2012-06-18
> **mountainman70 said:**
> Changed to Main Server and ran the commands and got same error. I am outside working and will check later to see if you have another step to try. Changed back to local server.

Thanks.

You could try re-installing dpkg using ```
sudo apt-get install --reinstall dpkg
``` but I am not sure what will happen if dpkg is broken,it might just fail again.

Good Luck

---

### Post by mountainman70 on 2012-06-18
> **plucky said:**
> You could try re-installing dpkg using ```
sudo apt-get install --reinstall dpkg
``` but I am not sure what will happen if dpkg is broken,it might just fail again.

Good Luck

This the last part and I don't know what it means or how to fix it. 

Preparing to replace apt 0.8.13.2ubuntu4.4 (using .../apt_0.8.13.2ubuntu4.6_i386.deb) ...
Unpacking replacement apt ...
dpkg: ../../src/archives.c:968: tarobject: Assertion `r == stab.st_size' failed.
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
E: Sub-process /usr/bin/dpkg exited unexpectedly

Any suggestions are appreciated.

---

### Post by NotSoRandomUsername on 2012-06-18
Try apt-get autoremove. If that doesnt work try going into recovery mode log in as root and running it again.

---

### Post by jmfal on 2012-06-18
While you are in recovery mode try

```
 sudo dpkg  --configure  -a      
```

---

### Post by mountainman70 on 2012-06-18
> **jmfal said:**
> While you are in recovery mode try

```
 sudo dpkg  --configure  -a      
```

Tried recovery mode and got this:
dpkg: ../../src/archives.c:968: tarobject: Assertion `r == stab.st_size' failed. 
 dpkg-deb: error: subprocess paste was killed by signal (Broken pipe) 
 Processing triggers for man-db ... 
 
Tried some other things and keep getting a warning that I need to run:

sudo dpkg --configure -a

Round and round I go.
Think i tried to run sudo apt-get install --reinstall dpkg. Not sure now so I will try it in recovery mode to see what happens. Any other thing I can try. 

Every thing was working the first of last week when I got some updates and they installed OK.
I am running this ubuntu on a seperate HD from a usb port, if that makes any difference.

---

### Post by jmfal on 2012-06-18
Hi Mountainman

Try that in a terminal again
```
sudo dpkg  --configure  -a  
```

Two spaces between dpkg and"--"
and two spaces between  "configure " and  "-a" (minus quoted

Sometimes if the syntax is incorrect command will not work

---

### Post by mountainman70 on 2012-06-18
> **jmfal said:**
> Hi Mountainman

Try that in a terminal again
```
sudo dpkg  --configure  -a  
```Two spaces between dpkg and"--"
and two spaces between  "configure " and  "-a" (minus quoted

Sometimes if the syntax is incorrect command will not work

Did not work. Thanks anyway. I think my dpkg is broken somehow because everything I try goes around in a circle.

---

### Post by jmfal on 2012-06-18
I had the same problem and it was fixed

restart to grub screen and select recovery > select "try to fix broken packages" >follow prompts for yes/no >enter > if screen tells you to run command manually, enter command at prompt  > press enter > enter password (you wil not see it on screen) > press enter

When its done select "resume normal boot"..

---

### Post by mountainman70 on 2012-06-18
> **jmfal said:**
> I had the same problem and it was fixed

restart to grub screen and select recovery > select "try to fix broken packages" >follow prompts for yes/no >enter > if screen tells you to run command manually, enter command at prompt  > press enter > enter password (you wil not see it on screen) > press enter

When its done select "resume normal boot"..

At the prompt I click Y and then enter and it runs and at the end I get this again:

dpkg: ../../src/archives.c:968: tarobject: Assertion `r == stab.st_size' failed. 
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)

---

### Post by jmfal on 2012-06-18
I'm running out of options.

Was that an regular update, or an update for a ppa that was installed recently?

---

### Post by mountainman70 on 2012-06-18
> **jmfal said:**
> I'm running out of options.

Was that an regular update, or an update for a ppa that was installed recently?

If you are asking about the last update, I don't remember. I think there were several of them.
As an added note. I have just install 11.04 on another HD and D/Led 296 updates. Everything went smooth. I think I will just add all my other things back to that HD. It will be a little time consuming getting all my settings back, but maybe easier than fooling with the other one. 
Thanks for all your help, but I am just going in circles trying to fix the broke one.

---

