---
title: "How to verify if manual installation is indeed installed?"
date: 2011-09-05
forum: General Help
---

### Post by ponch on 2011-09-05
Hi,

I'm 'new' to linux so please bear with me as I ask what is probably a simple question(s).

I seem to be having a dependency problem when trying to do an installation using the Package installer.  When I double click the package, the window opens and it seems to be working, then I get the following error: 

Error: Dependency is not satisfiable: libusb-1.0-0 ( >= 2:1.0.8 )

I downloaded the libusb 1.0.8 source, compiled and installed it. From the directory that I downloaded it to I ran ./configure, make, install and got the same error.  I then tried sudo ./configure, sudo make, sudo make install and still get the error.  

As far as I can tell it installed correctly and that is where my question is.  Is there a way for me to verify that it was installed correctly?

I have googled, searched the libusb website, and many others, but I haven't found anything showing how to verify that the installation was done correctly.

At this point, I don't know if I am just missing something that I need to do post installation or if I am just not doing it correctly to begin with.

Also, for what it's worth, the software I'm trying to install is Heimdall and Heimdall front end so I can flash my droid phone.

It has been a frustrating last few days so any help would be very much appreciated.

Thanks in advance.

---

### Post by Bobhuber on 2011-09-05
> **ponch said:**
> Hi,

I'm 'new' to linux so please bear with me as I ask what is probably a simple question(s).

I seem to be having a dependency problem when trying to do an installation using the Package installer.  When I double click the package, the window opens and it seems to be working, then I get the following error: 

Error: Dependency is not satisfiable: libusb-1.0-0 ( >= 2:1.0.8 )

I downloaded the libusb 1.0.8 source, compiled and installed it. From the directory that I downloaded it to I ran ./configure, make, install and got the same error.  I then tried sudo ./configure, sudo make, sudo make install and still get the error.  

As far as I can tell it installed correctly and that is where my question is.  Is there a way for me to verify that it was installed correctly?

I have googled, searched the libusb website, and many others, but I haven't found anything showing how to verify that the installation was done correctly.

At this point, I don't know if I am just missing something that I need to do post installation or if I am just not doing it correctly to begin with.

Also, for what it's worth, the software I'm trying to install is Heimdall and Heimdall front end so I can flash my droid phone.

It has been a frustrating last few days so any help would be very much appreciated.

Thanks in advance.
I'm not sure what version of Ubuntu you are using but Natty already has 1.08 as default. You will also most likely need to install (via synaptic) libusb-1.0-0-dev and libusb-dev  to do what you are trying to do. FYI you should copy , install and compile source files from your home directory as root. I believe the lib files in your case would be put in /usr/local/lib after the make install but I may be wrong.

---

### Post by ponch on 2011-09-06
Thanks Bobhuber for the reply.

Sorry I forgot to mention that I'm running Lucid Lynx and according to synaptic it looks like I have libusb-0.0-4, libusb-1.0-0, and libusb-dev installed.

I did just notice that there is a libusb-1.0-0-dev that is not installed.  I'm going to install that and also put the source files where you had suggested.  I'll post the results after I try the above.

Thanks again,

Tommy

---

### Post by fdrake on 2011-09-06
maybe the library is installed but the installer cannot find it?
to locate the library try:

```
locate libusb
```
you may have to change your $path variable to make sure that the installer finds the library. I am running lucid too. What kind of program are you installing ? Maybe i can guide you trough the installation..

*.dev packages stand for development and is used for developers to build and code the app. It won't make any effect installing it, in your case.

---

### Post by ponch on 2011-09-06
Thanks fdrake,

I did the locate libusb and it looks like I have something called libusb-0.1.so.4 and .so.4.4 and libusb-1.0.so.0 and .so.0.0.0

Both are located in /lib, /usr/lib, /usr/local/lib, and in my desktop folder where I had downloaded it to.

Is the proper location the /usr/local/lib directory?

The software I'm trying to install is called Heimdall. It's used for flashing roms on android phones.  The Samsung Fascinate in particular.

I'm hoping to give it another try in the next day or so and will post what I find.

Thanks again.

---

### Post by amir_pasha on 2011-10-18
I also run Ubuntu 10.04 and had dependency problem with libusb
but I guess I solved it with adding heimdall repository, so you have to do:

```
sudo add-apt-repository ppa:modycz/heimdall
```
then
check updates in Update Manager or run:
```
sudo apt-get update && sudo apt-get upgrade
```


(thank to [https://launchpad.net/~modycz/+archive/heimdall](https://launchpad.net/~modycz/+archive/heimdall))

---

### Post by ponch on 2011-10-21
Thank you amir_pasha.

I will give that a try this weekend just to see if I can get it work.

I have, in the mean time, 'solved' my problem by using the terminal instead of the gui for heimdall.

In the interest of answering my original question I think I will still try to resolve the dependency issue I was having and report back.

Thanks again.

---

### Post by fja0568 on 2011-10-28
> **amir_pasha said:**
> I also run Ubuntu 10.04 and had dependency problem with libusb
but I guess I solved it with adding heimdall repository, so you have to do:

```
sudo add-apt-repository ppa:modycz/heimdall
```then
check updates in Update Manager or run:
```
sudo apt-get update && sudo apt-get upgrade
```
(thank to [https://launchpad.net/~modycz/+archive/heimdall]("https://launchpad.net/%7Emodycz/+archive/heimdall"))

Thanks, this worked for me!

---

