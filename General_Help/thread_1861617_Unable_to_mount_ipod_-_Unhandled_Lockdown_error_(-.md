---
title: "Unable to mount ipod - Unhandled Lockdown error (-5)"
date: 2011-10-15
forum: General Help
---

### Post by Meelad on 2011-10-15
My ipod touch with iOS 4.3.3 doesn't mount on Ubuntu 11.10..

It gives me the following error:

Unable to mount ipod
Unhandled Lockdown error (-5)



Any ideas??

---

### Post by Meelad on 2011-10-15
I found the solution.. Install iFuse and then do this:

```
sudo apt-get install libimobiledevice-utils
idevicepair unpair && idevicepair pair
```

---

### Post by hunterm4573r on 2011-10-15
I had the same error and idevicepair worked for me running Ubuntu 11.10 x64 (I installed ifuse & libimobiledevice-utils together)

```
sudo apt-get install ifuse libimobiledevice-utils
idevicepair unpair && idevicepair pair
```

---

### Post by Meelad on 2011-10-15
> **hunterm4573r said:**
> I had the same error and idevicepair worked for me running Ubuntu 11.10 x64 (I installed ifuse & libimobiledevice-utils together)

```
sudo apt-get install ifuse libimobiledevice-utils
idevicepair unpair && idevicepair pair
```

Which confirms that this solution indeed fixes it.

Thanks for sharing... Moving on to the next problem (the default application). :D

---

### Post by Samanathon on 2011-10-16
I am having the same problem. When I try to repair, I get the following error:

```
QueryType failed, error code -256
```

Any ideas?

Thanks!

---

### Post by wim.glenn on 2011-10-19
Thanks, I had the same problem and your solution solved it immediately!

---

### Post by rscow on 2011-10-19
That solution worked for me with an iOS 5 iphone 4 and Oneiric.

Sweet.  Thanks.

Roger

---

### Post by primalsmoke on 2011-10-21
I used the ifuse solution, first time around worked.
Just wanted to say THANK YOU.
:D

---

### Post by matt_symes on 2011-10-21
Hi

> **Samanathon said:**
> I am having the same problem. When I try to repair, I get the following error:

```
QueryType failed, error code -256
```Any ideas?

Thanks!

From [http://libimobiledevice.sourcearchive.com/documentation/1.1.1-2/include_2libimobiledevice_2lockdown_8h_source.html](http://libimobiledevice.sourcearchive.com/documentation/1.1.1-2/include_2libimobiledevice_2lockdown_8h_source.html)

#define LOCKDOWN_E_UNKNOWN_ERROR            -256

Maybe you could use strace and see where it fails. That will tell you the problematic function.

Kind regards

---

### Post by followurdrmz on 2011-10-23
> **hunterm4573r said:**
> I had the same error and idevicepair worked for me running Ubuntu 11.10 x64 (I installed ifuse & libimobiledevice-utils together)

```
sudo apt-get install ifuse libimobiledevice-utils
idevicepair unpair && idevicepair pair
```

Works on ipod touch 3G on ios5. Using Rhythm box on Ubuntu 11.10.

---

### Post by 1clue on 2011-10-25
This does NOT work for my iPhone 3GS on IOS 5 with Ubuntu 11.04

Still gets the -15 error.

---

### Post by 300Z on 2011-10-29
Unhandled lockdown error (-4) on my 3GS running iOS5. :(

---

### Post by daveman67 on 2011-10-29
Hi - can anyone actually sync music with iOS5 and 11.10 (with rhythmbox or banshee)?

Both apps can see the iphone, but any music I copy over doesn't show up on the phone.

---

### Post by 300Z on 2011-10-29
I can't even access mine on nautilus or banshee at all and I'm stuck with no songs on mine because the iOS5 update whipped everything out. :(

---

### Post by Yogotiss on 2011-10-30
> **Meelad said:**
> I found the solution.. Install iFuse and then do this:

```
sudo apt-get install libimobiledevice-utils
idevicepair unpair && idevicepair pair
```

Thank you so much!

---

### Post by 300Z on 2011-10-30
I tried that too but now it doesn't even recognize that the device is plugged in.

---

### Post by catmandog on 2011-10-31
Brilliant. 
I was then able to log onto IOS5 and reinstall "camera roll"
Ubuntu Rocks.

---

### Post by shortpplerule on 2011-10-31
I've been trying to put music onto my iPhone but I've been unable to actually transfer songs from my computer onto the iPhone using all the programs that have been suggested like banshee and rhythmn box. When I try to transfer the songs, the applications supposedly converts the files and syncs it onto my iPhone but the syncing process isn't reflected on my iPhone nor does it contain any of the songs I try to transfer. I am running Ubuntu 11.10 64-bit and have an iPhone 4s iOS 5.0. Hopefully there is a fix for this in the next couple weeks.

---

### Post by InTheNameOfDelicious on 2011-11-01
Thanks a lot, this solved [_my problem_]("http://ubuntuforums.org/showthread.php?t=1873035&highlight=iphone") too.

---

### Post by altjx on 2011-11-03
Still also getting this error as well. >_<. The more I try pulling from Windows, the more errors I get :(

---

### Post by serpicojam on 2011-11-06
Tried all of this to no avail. iPhone 3GS with iOS 5, ubuntu 10.04. Error comes when I attempt the idevicepair unpair. I get error code -256. Getting bummed out! :confused:

---

### Post by quincey4 on 2011-11-09
> **Samanathon said:**
> I am having the same problem. When I try to repair, I get the following error:

```
QueryType failed, error code -256
```Any ideas?

Thanks!

I also had this issue.  I found a bug report referencing the '-5' error that looked like it was resolved with an update to libimobiledevice.  libimobiledevice-utils was already up to date so I just went ahead and installed the following packages:

sudo apt-get install libimobiledevice2-dbg libimobiledevice-dev libimobiledevice-doc libimobiledevice2

and voila!  Success!

I welcome any tips or instruction on how I could have handled this more elegantly than just installing every package synaptic showed containing "libimobiledevice*"

---

### Post by serpicojam on 2011-11-10
Anybody know of a fix for Lucid / 3GS with iOS 5?

---

### Post by caph1993 on 2011-11-23
Had the same problem, Ubuntu 11.10 32bits, iPod 4s 5.0.1.
Also worked for me:
sudo apt-get install ifuse libimobiledevice-utils idevicepair unpair && idevicepair pair
-Reconnect iPod
Thanks.

---

### Post by Juan Pablo Díaz Guerrero on 2011-11-27
Thanks for the Help!

It work!:)

---

### Post by griso8v on 2011-11-27
I'm still having this issue. Tried the other solutions but no result. Still getting "unable to mount iPod Touch; Unhandled Lockdown error (-15).
I'm using an iPod touch with Ubuntu 11.10 32bit. 
A little new to this, so the code suggestions before that broke across two lines, I don't think I was copying and pasting correctly. I've got iFuse installed, but haven't had any success with the libraries. Are the two lines of codes supposed to be one?
Any/all suggestions welcome. Please help.

---

### Post by jdix123 on 2011-12-01
I'm having a similar issue.

```

jasond@Natalie:~$ sudo apt-get install ifuse libimobiledevice-utils
[sudo] password for jasond: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  ifuse libimobiledevice-utils
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 73.0 kB of archives.
After this operation, 348 kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu/ oneiric/universe ifuse amd64 1.1.1-2 [14.3 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ oneiric-updates/universe libimobiledevice-utils amd64 1.1.1-1ubuntu1 [58.7 kB]
Fetched 73.0 kB in 0s (83.5 kB/s)              
Selecting previously deselected package ifuse.
(Reading database ... 220339 files and directories currently installed.)
Unpacking ifuse (from .../ifuse_1.1.1-2_amd64.deb) ...
Selecting previously deselected package libimobiledevice-utils.
Unpacking libimobiledevice-utils (from .../libimobiledevice-utils_1.1.1-1ubuntu1_amd64.deb) ...
Processing triggers for man-db ...
Setting up ifuse (1.1.1-2) ...
Setting up libimobiledevice-utils (1.1.1-1ubuntu1) ...
jasond@Natalie:~$ idevicepair unpair && idevicepair pair
SUCCESS: Unpaired with device 95dcab74ad256f37dcc2ee4f9fab0be632f09a28
SUCCESS: Paired with device 95dcab74ad256f37dcc2ee4f9fab0be632f09a28

```

But I'm still having the "unhandled lockdown error -15" when I plug it in.

What is the error?  Why can I see what the device is called but it won't mount?

I've got an iPod Touch 3G with iOS 5.0.1, Ubuntu 11.10 64 bit.

---

### Post by griso8v on 2011-12-03
I get a slightly different issue now with the code. It runs fine, but doesn't install anything. 
```
griso8v@desktop:~$ sudo apt-get install ifuse libimobiledevice-utils
[sudo] password for griso8v: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ifuse is already the newest version.
libimobiledevice-utils is already the newest version.
The following packages were automatically installed and are no longer required:
  libgladeui-1-11 linux-headers-3.0.0-12 linux-headers-3.0.0-12-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```For newly installed, my results are zero. Nothing else happens. End of line. I didn't have the iPod connected at the time of running the code. Should I have?

---

### Post by sectshun8 on 2011-12-07
Awesome.. that little fix worked perfectly :)

---

### Post by dmp2010 on 2011-12-07
Still doesn't work. Why doesn't Ubuntu has to make things like tihs easy, not difficult.

---

### Post by j1gs4w88 on 2011-12-11
for people are have done the follow:  ```
sudo apt-get install libimobiledevice-utils 
idevicepair unpair && idevicepair pair
```  and still get:  ```
 Unhandled Lockdown error (-5)
```  unlock the device first, by this i mean, slide to unlock and enter the 4 digit code if needed, and then try:  ```
 idevicepair unpair && idevicepair pair
```  unplug th device from pc and plug back in (make sure still unlocked) and all should be good

---

### Post by 300Z on 2011-12-11
Tried that and got "QueryType failed, error code -256"

---

### Post by hippy1970 on 2011-12-12
Worked for me too.
Only thing I would add is that I copied and pasted both the apt-get line and the idevicepair line at the same time. Which didn't work.
So enter them separately.

Many thanks!

Glenn:popcorn:

---

### Post by msumurph on 2011-12-17
> **j1gs4w88 said:**
> for people are have done the follow:  ```
sudo apt-get install libimobiledevice-utils 
idevicepair unpair && idevicepair pair
```  and still get:  ```
 Unhandled Lockdown error (-5)
```  unlock the device first, by this i mean, slide to unlock and enter the 4 digit code if needed, and then try:  ```
 idevicepair unpair && idevicepair pair
```  unplug th device from pc and plug back in (make sure still unlocked) and all should be good

@j1gs4w88 Thanks!  This worked for me.  Unlocking was the key.  Why didn't I think of that? :D

---

### Post by 1clue on 2011-12-17
> **j1gs4w88 said:**
> unlock the device first, by this i mean, slide to unlock and enter the 4 digit code if needed, and then try:  ```
 idevicepair unpair && idevicepair pair
```  unplug th device from pc and plug back in (make sure still unlocked) and all should be good

I can't believe it.  I feel incredibly stupid right now.

Unlock the @#$@ phone.

who'da thunk it?
](*,)

---

### Post by Jack9099 on 2011-12-23
For all you guys getting the Unhandled 256 error (Because You have ios5, I think) 
You will need the git version of libimobiledevice, just tested it on Arch Linux ;)

I have attached a screeny (and hidden my UUID)

---

### Post by shelbyvision on 2012-01-01
I have Ubuntu 10.04, and I have tried everything suggested here, and now, when the ipod is plugged in, NOTHING happens. Before I started messing with it, when I plugged it in, I got a menu that asked if I wanted to open it in rhythmbox, and when I clicked it I could open rhythmbox would open and the ipod icon would be there, it just wouldn't work. Now, nothing at all. I tried the last suggestion, running the code,  idevicepair unpair && idevicepair pair, with ipod plugged in, and it gave me this: [SIZE="2"]QueryType failed, error code -256[/SIZE]. Is there anything left to try? I don't understand why other people seem to get theirs to work and I can't. :(

---

### Post by 1clue on 2012-01-01
Did you unlock the iphone the same way you would when you make a call?

---

### Post by serpicojam on 2012-01-03
> **shelbyvision said:**
> I have Ubuntu 10.04, and I have tried everything suggested here, and now, when the ipod is plugged in, NOTHING happens. Before I started messing with it, when I plugged it in, I got a menu that asked if I wanted to open it in rhythmbox, and when I clicked it I could open rhythmbox would open and the ipod icon would be there, it just wouldn't work. Now, nothing at all. I tried the last suggestion, running the code,  idevicepair unpair && idevicepair pair, with ipod plugged in, and it gave me this: [SIZE="2"]QueryType failed, error code -256[/SIZE]. Is there anything left to try? I don't understand why other people seem to get theirs to work and I can't. :(
I too am working with 10.04 and have had no luck since upgrading my iPhone to iOS 5. I think the problem is with 10.04, as folks working with 11.x are having some success, unless somebody out there has a solution . . .

---

### Post by kaylus on 2012-01-04
> **quincey4 said:**
> I also had this issue.  I found a bug report referencing the '-5' error that looked like it was resolved with an update to libimobiledevice.  libimobiledevice-utils was already up to date so I just went ahead and installed the following packages:

sudo apt-get install libimobiledevice2-dbg libimobiledevice-dev libimobiledevice-doc libimobiledevice2

and voila!  Success!

I welcome any tips or instruction on how I could have handled this more elegantly than just installing every package synaptic showed containing "libimobiledevice*"

With the original posters installation and this the errors went away on the iPod 4G. Cheers! It definitely could have probably been handled without the doc and dbg files, and likely without the dev files but I don't care -- as long as it works. I don't mind a bit of clutter ... makes me feel like I'm at home.

---

### Post by kaylus on 2012-01-04
> **shelbyvision said:**
> I have Ubuntu 10.04, and I have tried everything suggested here, and now, when the ipod is plugged in, NOTHING happens. Before I started messing with it, when I plugged it in, I got a menu that asked if I wanted to open it in rhythmbox, and when I clicked it I could open rhythmbox would open and the ipod icon would be there, it just wouldn't work. Now, nothing at all. I tried the last suggestion, running the code,  idevicepair unpair && idevicepair pair, with ipod plugged in, and it gave me this: [SIZE="2"]QueryType failed, error code -256[/SIZE]. Is there anything left to try? I don't understand why other people seem to get theirs to work and I can't. :(

Another poster mentioned exactly what to do when confronted with this code, in this forum. Have you read the entire forum and tried it?

Perhaps it needs to be summed up:

1. sudo apt-get install libimobiledevice-utils 
   idevicepair unpair && idevicepair pair

If after doing this you receive QueryType failed, error code -256. You need to install libimobiledevice2. A previous poster mentioned installing the GIT version of it. Another poster mentioned:

2. sudo apt-get install libimobiledevice2-dbg libimobiledevice-dev libimobiledevice-doc libimobiledevice2

3. idevicepair unpair && idevicepair pair

---

Note, I just verbatim copied the previous poster. It's likely you don't need to install the -dbg, -dev, and -doc files. If you are running 10.04 then please get the newest version of libimobiledevice2 and it's dependencies in whichever way you feel necessary.

This fixed my issue on IOS 5.0

Kind Regards,
Kaylus

---

### Post by bry5318 on 2012-01-04
I get: 

error opening socket!  
no device found, is it plugged in?  (yes, i have it plugged in)

Help!

---

### Post by stivan on 2012-01-07
> **quincey4 said:**
> I also had this issue.  I found a bug report referencing the '-5' error that looked like it was resolved with an update to libimobiledevice.  libimobiledevice-utils was already up to date so I just went ahead and installed the following packages:

sudo apt-get install libimobiledevice2-dbg libimobiledevice-dev libimobiledevice-doc libimobiledevice2

and voila!  Success!

I welcome any tips or instruction on how I could have handled this more elegantly than just installing every package synaptic showed containing "libimobiledevice*"

As you said my friend VOILA!!!!

Thanks!!! iphone 4 iOS 5.0.1 Ubuntu 11.10

---

### Post by Llewxam on 2012-01-07
same issues here with 3gs and 5.0.1 in 10.04
can't get git version installed nor libimobiledevice2. any help?

---

### Post by leifharmsen on 2012-01-31
I'm using Ubuntu 11.04 and have libimobiledevice installed.  When I try to apt-get install libimobiledevice2 I get:

E: Unable to locate package libimobiledevice2

Do I have to add a repository or something to get this?

---

### Post by ktm91 on 2012-02-01
> **kaylus said:**
> Another poster mentioned exactly what to do when confronted with this code, in this forum. Have you read the entire forum and tried it?

Perhaps it needs to be summed up:

1. sudo apt-get install libimobiledevice-utils 
   idevicepair unpair && idevicepair pair

If after doing this you receive QueryType failed, error code -256. You need to install libimobiledevice2. A previous poster mentioned installing the GIT version of it. Another poster mentioned:

2. sudo apt-get install libimobiledevice2-dbg libimobiledevice-dev libimobiledevice-doc libimobiledevice2

3. idevicepair unpair && idevicepair pair

---

Note, I just verbatim copied the previous poster. It's likely you don't need to install the -dbg, -dev, and -doc files. If you are running 10.04 then please get the newest version of libimobiledevice2 and it's dependencies in whichever way you feel necessary.

This fixed my issue on IOS 5.0

Kind Regards,
Kaylus

ehmm I have 10.04 and I can't find a libimobiledevice2 packet for my version.. can you tell me how you installed it please? thanks a lot!

---

### Post by d4m1r on 2012-02-03
Thank you!!!

It is working better now with iOS 5.0.1 (jailbroken) and 11.10 than it even was with 4.3.x and 11.04 :mrgreen:

---

### Post by sanjito on 2012-02-04
> **kaylus said:**
> Another poster mentioned exactly what to do when confronted with this code, in this forum. Have you read the entire forum and tried it?

Perhaps it needs to be summed up:

1. sudo apt-get install libimobiledevice-utils 
   idevicepair unpair && idevicepair pair

If after doing this you receive QueryType failed, error code -256. You need to install libimobiledevice2. A previous poster mentioned installing the GIT version of it. Another poster mentioned:

2. sudo apt-get install libimobiledevice2-dbg libimobiledevice-dev libimobiledevice-doc libimobiledevice2

3. idevicepair unpair && idevicepair pair

---

Note, I just verbatim copied the previous poster. It's likely you don't need to install the -dbg, -dev, and -doc files. If you are running 10.04 then please get the newest version of libimobiledevice2 and it's dependencies in whichever way you feel necessary.

This fixed my issue on IOS 5.0

Kind Regards,
Kaylus

This worked perfectly. Thank you so much.

---

### Post by jpborjas on 2012-02-07
It worked for me. Thanks!

---

### Post by DreamcasterTM on 2012-02-09
> **hunterm4573r said:**
> I had the same error and idevicepair worked for me running Ubuntu 11.10 x64 (I installed ifuse & libimobiledevice-utils together)

```
sudo apt-get install ifuse libimobiledevice-utils
idevicepair unpair && idevicepair pair
```

Thank you!
That worked for me as well (iPod touch 2G on Ubuntu 11.10)
I had to input each command at once, though.
Does anyone know why?
```
sudo apt-get install ifuse
```
+
```
sudo apt-get libimobiledevice-utils
```
+
```
devicepair unpair && idevicepair pair
```

Plus, another strange thing: I have just reinstalled Ubuntu yesterday, while this problem with my iPod wasn't there 2 days ago...same computer, same Ubuntu version, same updates installed...

Go figure...

---

### Post by WoollyW on 2012-02-15
I'm getting this exact same thing - tried the pair & unpair trick through terminal and it simply says "no device found, is it plugged in?" which of course it is.

The phone charges through the cable, and a Windows OS will see it & mount it, so I know it's not the cable. 

I'm running 11.04 64bit, jailbreak iPhone 3G, 4.2.1.

This can't be another 64bit problem, can it?

---

### Post by ssonic on 2012-02-16
it looks like libimobiledevice2 should be installed, but 2nd version available only from 11.04 on due to dependencies.

on 10.10 no solution found

---

### Post by darkschine on 2012-02-21
> **matt_symes said:**
> Hi



From [http://libimobiledevice.sourcearchive.com/documentation/1.1.1-2/include_2libimobiledevice_2lockdown_8h_source.html](http://libimobiledevice.sourcearchive.com/documentation/1.1.1-2/include_2libimobiledevice_2lockdown_8h_source.html)

#define LOCKDOWN_E_UNKNOWN_ERROR            -256

Maybe you could use strace and see where it fails. That will tell you the problematic function.

Kind regards

I am having the same problems. strace hinted that I needed to install usbmuxd. Now I am stuck here:

fstat64(1, {st_mode=S_IFCHR|0620, st_rdev=makedev(136, 0), ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb78e9000
write(1, "QueryType failed, error code -25"..., 34QueryType failed, error code -256


I'm using Ubuntu 11.04

---

### Post by jmans25 on 2012-02-26
> **quincey4 said:**
> I also had this issue.  I found a bug report referencing the '-5' error that looked like it was resolved with an update to libimobiledevice.  libimobiledevice-utils was already up to date so I just went ahead and installed the following packages:

sudo apt-get install libimobiledevice2-dbg libimobiledevice-dev libimobiledevice-doc libimobiledevice2

and voila!  Success!

I welcome any tips or instruction on how I could have handled this more elegantly than just installing every package synaptic showed containing "libimobiledevice*"

THANKS!!! solved my problem.

---

### Post by motoso on 2012-03-16
Hi, I've tried all the solutions above, but can't get my music to show up on my ipod touch 4G with IOS 5.1 and Ubuntu 11.10. I'm using Banshee also.

Has anybody had success adding music?

I hate Apple for being so uptight about their software.

---

### Post by squee on 2012-03-17
> **motoso said:**
> Hi, I've tried all the solutions above, but can't get my music to show up on my ipod touch 4G with IOS 5.1 and Ubuntu 11.10. I'm using Banshee also.

Has anybody had success adding music?

I hate Apple for being so uptight about their software.

My iPod is recognised, and it appears to convert/transfer/sync files but nothing actually appears.

Interestingly, I deleted an album. It is still listed on the iPod but nothing ever plays. Perhaps a database updating issue? 

Help would be really appreciated, I really don't want to have to reboot into windows just to add music to my mp3 player!

---

### Post by xanaftp on 2012-05-23
Hello. I have the newest iPod Touch with iOS 5.1.1 I think... and Ubuntu [studio] 11.10.

I have tried EVERY suggestion in this forum and nothing at all has worked... not even getting any error messages. The iPod simply will not mount/be recognized by Ubuntu. I even went into disk utility and it is not there. Yes, my iPod is unlocked when I did this, and yes I did the unpair, pair, validate, and reconnect iPod all while iPod was unlocked. I installed ifuse and the mobiledevice libraries. I tried Rhythmbox, Amarok, and Banshee, and nothing is showing the iPod Touch is connected.

Any help would greatly be appreciated!

---

### Post by tango_ninja on 2012-06-02
> **hunterm4573r said:**
> I had the same error and idevicepair worked for me running Ubuntu 11.10 x64 (I installed ifuse & libimobiledevice-utils together)

```
sudo apt-get install ifuse libimobiledevice-utils
idevicepair unpair && idevicepair pair
```

This worked for me as well

---

### Post by fendijr on 2012-06-07
> **Meelad said:**
> I found the solution.. Install iFuse and then do this:

```
sudo apt-get install libimobiledevice-utils
idevicepair unpair && idevicepair pair
```


here what i always got for all others solution too..

fendi@fendi-Aspire-4925:~$ sudo apt-get install libimobiledevice-utils
[sudo] password for fendi: 
Sorry, try again.
[sudo] password for fendi: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  libimobiledevice-utils
0 upgraded, 1 newly installed, 0 to remove and 298 not upgraded.
/usr/lib/apt/methods/http: 2: /usr/bin/trickle: not found
E: Method http has died unexpectedly!
E: Sub-process http returned an error code (127)
E: Method /usr/lib/apt/methods/http did not start correctly
fendi@fendi-Aspire-4925:~$

---

### Post by TimothyMagee on 2012-07-21
I am using Lucid Linux, and ipod Touch  5.0.1 and I seem to have the same problem.  I ran idevicepair unpair && idevicepair pair. it gave me lockdown error 256. I did it with debug on and here is what it said:


[I]09:11:38 lockdown.c:308 lockdownd_query_type(): called
09:11:38 property_list_service.c:142 internal_plist_send(): sending 284 bytes
09:11:38 property_list_service.c:147 internal_plist_send(): sent 284 bytes
09:11:38 property_list_service.c:148 internal_plist_send(): printing 284 bytes plist:
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
    <key>Label</key>
    <string>idevicepair</string>
    <key>Request</key>
    <string>QueryType</string>
</dict>
</plist>
09:11:38 property_list_service.c:224 internal_plist_receive_timeout(): initial read=4
09:11:38 property_list_service.c:233 internal_plist_receive_timeout(): 297 bytes following
09:11:38 property_list_service.c:242 internal_plist_receive_timeout(): received 297 bytes
09:11:38 property_list_service.c:256 internal_plist_receive_timeout(): printing 297 bytes plist:
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
    <key>Request</key>
    <string>QueryType</string>
    <key>Type</key>
    <string>com.apple.mobile.lockdown</string>
</dict>
</plist>
[/I]

---

### Post by dr1094 on 2012-08-26
please help,
ok, my problem is a different, and might lead to a better solution (iHope).
problem: unhandled lockdown....(-15)

[*I just want to say in advance that I do not want to install any additional software as you will see from my description, that I probably don't need to.*]

I have iPhone 3gs (16 Gig), running iOS 5.1.1, and an iPhod Touch 1st Gen running iOS 3.1.2.

I have 3 usernames on my laptop. userA, userB, userC

The iPhone is not detected on only one username (usernameB), it is connected perfectly on other usernames (A&C) on the same machine. 
However, the iPod connects on usernameB perfectly. 

'So What may I have done to preferences on usernameB, so that iPhone is not connecting?'
'or do I need to change something on the iphone'
'or do i really have to install additonal software, since it works anyway on other usernames, i mean i can't just uninstall a software from one username (can i?)'

Other details: 
- the iphone does charge
- cannot see iphone under disk utility- 
- CAN see iphone in terminal: lsusb
- iphone is jailbroken
- before the iphone use to show up in two parts: One was called 'user's iPhone', and other was called 'Document's on user's iPhone'. This is how the iPod stil shows up. However, the iPhone shows up as one directory, called user's iPhone. but it is unaccessible due to error, as above.
- let me know if you need more details


Thanks for any answers, I appreciate all responses.

---

### Post by dreville on 2012-11-15
First I tried:

```
sudo apt-get install ifuse
```

Unplugged, plugged and still got unhandled error. Got to this page and tried:

```
sudo apt-get install libimobiledevice-utils
sudo apt-get install libimobiledevice-utils
```

Unplugged, plugged and still got unhandled error. Then a further post said:

```
sudo apt-get install libimobiledevice2-dbg libimobiledevice-dev libimobiledevice-doc libimobiledevice2
```

Unplugged, plugged then Ubuntu started asking me if I want to open pictures in Shotwell and music in Banshee. Works perfectly.

This is on Ubuntu 11.10 Server 64bit, iPhone 4, iOS6.0.1.

---

