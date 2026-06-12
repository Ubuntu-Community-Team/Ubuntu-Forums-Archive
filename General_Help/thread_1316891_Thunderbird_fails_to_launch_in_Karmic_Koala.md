---
title: "Thunderbird fails to launch in Karmic Koala"
date: 2009-11-06
forum: General Help
---

### Post by moooping on 2009-11-06
I'm relatively new to Ubuntu and have been happily running Jaunty for a couple of months. I upgraded to Karmic Koala yesterday and am now experiencing problems with launching Thunderbird: 

 When launching through Application>Internet>Mozilla Thunderbird, the program fails to load.
  Going thought Terminal I get the following message:
  

/opt/thunderbird/thunderbird-bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory  
 

 I checked in synaptic and have libstdc++6 installed.
 I removed and reinstalled thunderbird but the problem continues to exist.
 

 It looks like a similar issue is described here:[http://ubuntuforums.org/showthread.php?t=599452](http://ubuntuforums.org/showthread.php?t=599452) 
 

 I am running Thunderbird 2.0.0.23.
 

 Any help is truly appreciated!

 

 Many thanks!!

---

### Post by Nick Rhodes on 2009-11-06
I would suggest reinstalling Thunderbird, this should install the correct librarys, which is what the error you are getting is pointing at. It may not be Thunderbird itself, could be an Add-on that you have installed that causes Thunderbird to fail to load.

I would backup your Thunderbird folder in your home directory (it will be hidden and called ".thunderbird").

Then use Synaptic or command line to remove and reinstall.

Cheers, Nick

---

### Post by HiImTye on 2009-11-06
try
```
sudo apt-get remove libstdc++6 && sudo apt-get install libstdc++6
```

then try and load it

else replace 'remove' with 'purge'

---

### Post by moooping on 2009-11-06
Thanks - I have completely removed thunderbird and reinstalled but to no avail.

I have now tried to remove/purge libstdc++6 as suggested. I get the following output in terminal for both the remove or purge commands:

matthias@matthias-laptop:~$ sudo apt-get purge libstdc++6
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  lzma: Depends: libstdc++6 (>= 4.2.1) but it is not going to be installed
E: Broken packages

Unfortunately, I don't know what this means or where to go from here...

---

### Post by arnab_das on 2009-11-06
is this to do with 64 bit thingy?

also, switch to evolution. i really hated it in the beginning as i was always a thunderbird fan, but i've fallen i love with it once i gave it a real try. it also blends perfectly with the gnome interface.

---

### Post by moooping on 2009-11-06
Thanks - not sure what the 64b thingy is - I think I'm running 32bit.

Looks like I will have to experiment with evolution - I'll miss my old Thunderbird settings...:-(

---

### Post by XCan on 2009-11-06
> **moooping said:**
> Thanks - not sure what the 64b thingy is - I think I'm running 32bit.

Looks like I will have to experiment with evolution - I'll miss my old Thunderbird settings...:-(

You can check what you're running by typing ```
 uname -m 
``` If you're running 64 bit it will say x86_64.

---

### Post by finno on 2009-11-06
I don't have the laucnhpad link to bug available at the moment, but upgrade on old laptop left Thunderbird working fine. But on fresh install on new laptop, Thunderbird will not work on Karmic due to missing libraries.

---

### Post by wojox on 2009-11-06
I run Thunderbird 2.0.0.23 in Karmic just fine, downloaded from the repo's. Just wondering why is Thunderbird in your /opt directory? Did you download it from Mozilla?

---

### Post by Nick Rhodes on 2009-11-07
> **wojox said:**
> I run Thunderbird 2.0.0.23 in Karmic just fine, downloaded from the repo's. Just wondering why is Thunderbird in your /opt directory? Did you download it from Mozilla?

Would make sense as its asking for libC++5. Ubuntu version is built against libC++6.

Cheers, Nick.

---

### Post by ad_267 on 2009-11-07
Yeah, why aren't you using Thunderbird from the repositories? Install it from there and you'll be fine.

You might want to read this: [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by shiroyoshida on 2009-11-08
Hello all, 

I have the exact same problem only in my case Thunderbird was working fine yesterday when I upgraded from Jaunty to Karmic but it's not working today. I get the same error message when I'm trying to uninstall and reinstall the libstdc++6 library: 

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  lzma: Depends: libstdc++6 (>= 4.2.1) but it is not going to be installed
E: Broken packages

```and when I'm trying to start Thunderbird from the terminal this is the output I'm getting: 

```
** (gecko:4132): WARNING **: No listener with the specified listener id 1

** (gecko:4132): WARNING **: No listener with the specified listener id 2

** (gecko:4132): WARNING **: No listener with the specified listener id 3

** (gecko:4132): WARNING **: No listener with the specified listener id 4

** (gecko:4132): WARNING **: No listener with the specified listener id 5

** (gecko:4132): WARNING **: No listener with the specified listener id 6

** (gecko:4132): WARNING **: No listener with the specified listener id 7

** (gecko:4132): WARNING **: No listener with the specified listener id 8

** (gecko:4132): WARNING **: No listener with the specified listener id 9

** (gecko:4132): WARNING **: No listener with the specified listener id 10

** (gecko:4132): WARNING **: No listener with the specified listener id 11

** (gecko:4132): WARNING **: No listener with the specified listener id 12

** (gecko:4132): WARNING **: No listener with the specified listener id 13

** (gecko:4132): WARNING **: No listener with the specified listener id 14

** (gecko:4132): WARNING **: No listener with the specified listener id 15

** (gecko:4132): WARNING **: No listener with the specified listener id 16

** (gecko:4132): WARNING **: No listener with the specified listener id 17

** (gecko:4132): WARNING **: No listener with the specified listener id 18

** (gecko:4132): WARNING **: No listener with the specified listener id 19

** (gecko:4132): WARNING **: No listener with the specified listener id 20

** (gecko:4132): WARNING **: No listener with the specified listener id 21

** (gecko:4132): WARNING **: No listener with the specified listener id 22

** (gecko:4132): WARNING **: No listener with the specified listener id 23

** (gecko:4132): WARNING **: No listener with the specified listener id 24

** (gecko:4132): WARNING **: No listener with the specified listener id 25

** (gecko:4132): WARNING **: No listener with the specified listener id 26

** (gecko:4132): WARNING **: No listener with the specified listener id 27

** (gecko:4132): WARNING **: No listener with the specified listener id 28

** (gecko:4132): WARNING **: No listener with the specified listener id 29

(gecko:4132): GLib-CRITICAL **: g_hash_table_foreach_remove: assertion `hash_table != NULL' failed

(gecko:4132): GLib-CRITICAL **: g_hash_table_size: assertion `hash_table != NULL' failed
The program 'thunderbird-bin' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadWindow (invalid Window parameter)'.
  (Details: serial 1034 error_code 3 request_code 20 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
```Looking up the libstdc++5 in the repositories returns no results. Attempting to install it via the terminal returns this message: 

```
E: Invalid operation libstdc++5
```Shouldn't libstdc++6 be backwards-compatible? 

Starting Thunderbird  from the terminal seems to work but when the terminal window is closed, Thunderbird closes with it... 

I'm running a 64bit system by the way. If anyone could helps us out, I'd be very grateful! :D

Thank you.

---

### Post by Nick Rhodes on 2009-11-08
> **shiroyoshida said:**
> Hello all, 

I have the exact same problem only in my case Thunderbird was working fine yesterday when I upgraded from Jaunty to Karmic but it's not working today. I get the same error message when I'm trying to uninstall and reinstall the libstdc++6 library: 

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  lzma: Depends: libstdc++6 (>= 4.2.1) but it is not going to be installed
E: Broken packages

```and when I'm trying to start Thunderbird from the terminal this is the output I'm getting: 

```
** (gecko:4132): WARNING **: No listener with the specified listener id 1

** (gecko:4132): WARNING **: No listener with the specified listener id 2

** (gecko:4132): WARNING **: No listener with the specified listener id 3

** (gecko:4132): WARNING **: No listener with the specified listener id 4

** (gecko:4132): WARNING **: No listener with the specified listener id 5

** (gecko:4132): WARNING **: No listener with the specified listener id 6

** (gecko:4132): WARNING **: No listener with the specified listener id 7

** (gecko:4132): WARNING **: No listener with the specified listener id 8

** (gecko:4132): WARNING **: No listener with the specified listener id 9

** (gecko:4132): WARNING **: No listener with the specified listener id 10

** (gecko:4132): WARNING **: No listener with the specified listener id 11

** (gecko:4132): WARNING **: No listener with the specified listener id 12

** (gecko:4132): WARNING **: No listener with the specified listener id 13

** (gecko:4132): WARNING **: No listener with the specified listener id 14

** (gecko:4132): WARNING **: No listener with the specified listener id 15

** (gecko:4132): WARNING **: No listener with the specified listener id 16

** (gecko:4132): WARNING **: No listener with the specified listener id 17

** (gecko:4132): WARNING **: No listener with the specified listener id 18

** (gecko:4132): WARNING **: No listener with the specified listener id 19

** (gecko:4132): WARNING **: No listener with the specified listener id 20

** (gecko:4132): WARNING **: No listener with the specified listener id 21

** (gecko:4132): WARNING **: No listener with the specified listener id 22

** (gecko:4132): WARNING **: No listener with the specified listener id 23

** (gecko:4132): WARNING **: No listener with the specified listener id 24

** (gecko:4132): WARNING **: No listener with the specified listener id 25

** (gecko:4132): WARNING **: No listener with the specified listener id 26

** (gecko:4132): WARNING **: No listener with the specified listener id 27

** (gecko:4132): WARNING **: No listener with the specified listener id 28

** (gecko:4132): WARNING **: No listener with the specified listener id 29

(gecko:4132): GLib-CRITICAL **: g_hash_table_foreach_remove: assertion `hash_table != NULL' failed

(gecko:4132): GLib-CRITICAL **: g_hash_table_size: assertion `hash_table != NULL' failed
The program 'thunderbird-bin' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadWindow (invalid Window parameter)'.
  (Details: serial 1034 error_code 3 request_code 20 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
```Looking up the libstdc++5 in the repositories returns no results. Attempting to install it via the terminal returns this message: 

```
E: Invalid operation libstdc++5
```Shouldn't libstdc++6 be backwards-compatible? 

Starting Thunderbird  from the terminal seems to work but when the terminal window is closed, Thunderbird closes with it... 

I'm running a 64bit system by the way. If anyone could helps us out, I'd be very grateful! :D

Thank you.

You could try installing the Januty package from [http://packages.ubuntu.com/jaunty/libstdc+](http://packages.ubuntu.com/jaunty/libstdc+), there are i386 and AMD64 packages.

Cheers, Nick

---

### Post by shiroyoshida on 2009-11-08
Hello Nick, 

Installing the library from a source other than Synaptic didn't even cross my mind but I got the deb package from [http://packages.ubuntu.com/jaunty/libstdc++5](http://packages.ubuntu.com/jaunty/libstdc++5) and so far things seem to working just fine! 

The package even shows in Synaptic and can be removed as any other installed package/application in case it causes any problems. But let's hope that everything will be OK. ;)

Thank you very much for your help and I hope others will benefit from your suggestion.

---

