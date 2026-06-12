---
title: "No Groupwise Support for Evolution in 11.10?"
date: 2011-10-14
forum: General Help
---

### Post by WhiskoKid on 2011-10-14
It seems as if there is no Groupwise support in Evolution 3.2.0 in Ubuntu 11.10... that is my existing Groupwise setup in Evolution no longer works and there is no way to choose a Groupwise account when setting up a new account. Other distributions appear to have a package called "evolution-groupwise" which is the "GroupWise connector for evolution"

Is there some type of workaround available?
I don't really have a choice at work NOT to use Groupwise, and Evolution worked okay to manage email and calendar events.

---

### Post by crazymonkey on 2011-10-14
I am in the same situation as you are and I am not happy. Fortunately I have learned to test all the features I need in VM prior to upgrading my "production" installation and right now I stick with Natty until something is done to fix this.

I really hope there is some work around. I might investigate compiling evolution-groupwise by myself. 

I will let you know if I find something.

---

### Post by WhiskoKid on 2011-10-17
Okay so I found a workaround that seems to be working for the moment.

It appears that Arch Linux has the evolution-groupwise package that can be downloaded here:
[http://www.archlinux.org/packages/extra/i686/evolution-groupwise/](http://www.archlinux.org/packages/extra/i686/evolution-groupwise/)


So this is what I did to make it work again:
1) Create a new folder on the Desktop called "evolution-groupwise"
2) Download the Arch Linux evolution-groupwise package: [http://www.archlinux.org/packages/extra/i686/evolution-groupwise/download/](http://www.archlinux.org/packages/extra/i686/evolution-groupwise/download/)
3) Open the "evolution-groupwise-3.2.0-1-i686.pkg.tar.xz" file and copy the "usr" folder into the "evolution-groupwise" folder I created
4) Make a folder called "DEBIAN" inside the "evolution-groupwise" folder.
5) Create a .deb control file. Just copy the following text and place it into the file "evolution-groupwise/DEBIAN/control"
### begin paste
Package: evolution-groupwise
Version: 3.2.0-1-000000000000000000
Section: web 
Priority: optional
Architecture: i386
Depends: evolution-data-server, libgtkhtml-4.0-0
Recommends: evolution
Installed-Size: 884736
Maintainer: NOBODY
Description:  GroupWise connector for evolution
### end paste
6) Now go to the folder above where you created the evolution-groupwise folder and create a .deb package from these files... you will need "dkpg-deb" so if it doesn't work, try "sudo apt-get install dpkg-deb"
7) To create the package type "dpkg-deb --build evolution-groupwise" to make a .deb package from the "evolution-groupwise" folder
8) Now install the package "sudo dpkg -i evolution-groupwise.deb"

Note that this is on a 32-bit machine. To work on a 64 bit machine you would have to download the 64-bit package from Arch and change the Architecture to amd64 in the DEBIAN/control file.

Hopefully this is just a temporary hack and there will be an official version of this released soon.

---

### Post by bruhein on 2011-10-18
On a 64-bit machine the installation works fine - no errors, but Evolution complains while starting:

[FONT=Courier New]evolution-plugin-lib-WARNING **: can't load plugin '/usr/lib/evolution/3.2/plugins/liborg-gnome-groupwise-features': /lib/x86_64-linux-gnu/libc.so.6: version `GLIBC_2.14' not found (required by /usr/lib/evolution-data-server/camel-providers/libcamelgroupwise.so)[/FONT]

My (Ubuntu 11.10)[FONT=Courier New] libc.so.6[/FONT] links to [FONT=Courier New]libc-2.13.so[/FONT], but 2.14 is needed.
I little bit Google told me that libc-2.14 seems to be buggy (Seg faults).

But anyway a simple exchange of such a central lib must lead to problems...

Is there any other workaround?

---

### Post by dcstar on 2011-10-18
> **bruhein said:**
> On a 64-bit machine the installation works fine - no errors, but Evolution complains while starting:

[FONT=Courier New]evolution-plugin-lib-WARNING **: can't load plugin '/usr/lib/evolution/3.2/plugins/liborg-gnome-groupwise-features': /lib/x86_64-linux-gnu/libc.so.6: version `GLIBC_2.14' not found (required by /usr/lib/evolution-data-server/camel-providers/libcamelgroupwise.so)[/FONT]

My (Ubuntu 11.10)[FONT=Courier New] libc.so.6[/FONT] links to [FONT=Courier New]libc-2.13.so[/FONT], but 2.14 is needed.
I little bit Google told me that libc-2.14 seems to be buggy (Seg faults).

But anyway a simple exchange of such a central lib must lead to problems...

Is there any other workaround?

[LIST=1]
[*]Why did you use a 32 bit version on your 64 bit system?
[*]Why not just use the package from the previous Ubuntu release?
[/LIST]

---

### Post by bruhein on 2011-10-18
1) I am using the 64-bit version of the Arch package
2) The previous package is made for Evolution 2.xx. Now we are dealing with Evolution 3.2.0 - I did not dare to cut out Evolution 3.2 from Ubuntu 11.10 and downgrade to Evolution 2.xx

---

### Post by WhiskoKid on 2011-10-18
This is now reported as a bug: [https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/876563](https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/876563)

Hopefully an official package will come soon.

I am not sure what other workarounds there could be... 

One could try to compile directly from the source and use checkinstall to make a package, but I am just a hacker scientist so repackaging the Arch package was easier for me.

At least on 32-bit, this is still working for me. I can read, write, and send email with no obvious problems since yesterday. I am not able to access the calendar, but I can use the web client for that for now. Too bad this didn't work on 64-bit.

---

### Post by bruhein on 2011-10-18
Touchdown!

I made a build from the Gnome sources of evolution-groupwise-3.2.0 and it works.

1) Download [http://ftp.gnome.org/pub/GNOME/sources/evolution-groupwise/3.2/evolution-groupwise-3.2.0.tar.bz2](http://ftp.gnome.org/pub/GNOME/sources/evolution-groupwise/3.2/evolution-groupwise-3.2.0.tar.bz2) and unpack somewhere in your home directory an d open a terminal

2) Prepare (most) of the required build packages 
[FONT=Courier New]sudo apt-get build-dep evolution[/FONT]

3)Build 

[FONT=Courier New]cd evolution-groupwise-3.2.0

./configure
[/FONT]
If some packages are missing, install them by installing their '*-dev' versions
[FONT=Courier New]
make

sudo make install

[/FONT]That's it!

After setting up the Groupwise account, there might arise the problem already known from Natty:
"Host lookup failed: mail.xxx.de: Servname not supported for ai_socktype"

Just edit /etc/services and add the following entries (I am using the default port 1677 for Groupwise)

[FONT=Courier New]groupwise 1677/tcp[/FONT][FONT=Courier New]
groupwise 1677/udp[/FONT]

After a reboot I could connect to my mailbox.[FONT=Courier New] 
[/FONT]

---

### Post by bruhein on 2011-10-19
Unfortunately the calendar is not working using the upper solution.

[FONT=Courier New](evolution:12361): calendar-gui-DEBUG: get_view_cb: Failed to start view: Keine derartige Schnittstelle »org.gnome.evolution.dataserver.CalendarView« des Objekts im Pfad /org/gnome/evolution/dataserver/CalendarView/28439/4[/FONT]

Does anyone have an idea how to solve that?

---

### Post by bpedman on 2011-10-21
It took quite a while to figure out but I got the evolution-groupwise plugin compiled from source and appears to be working nicely. I get calendar and email.

I followed most of bruhein's steps for compiling from source. However, I noticed there was a bug that the SOAP port (for calendar I think) was always set to 0. So here is what I did:

1. Install git (sudo apt-get install git)
2. git clone git://git.gnome.org/evolution-groupwise
3. cd evolution-groupwise
4. git checkout -b 3.2.0-patch EVOLUTION_GROUPWISE_3_2_0
5. git cherry-pick 3aae80f55d5fd565274f19210564e74d5350a66c # This is the patch for the SOAP port bug
6. Open configure.ac, at about line 48 add the line AC_CHECK_LIB(gthread-2.0, g_thread_init)
7. sudo apt-get build-dep evolution
8. ./autogen.sh
9. make
10. sudo make install
11. Edit /etc/services like bruhein describes

That's it I think

---

### Post by bruhein on 2011-10-22
Thanx bpedman - it works for me too.

> **bpedman said:**
> It took quite a while to figure out but I got the evolution-groupwise plugin compiled from source and appears to be working nicely. I get calendar and email.

I followed most of bruhein's steps for compiling from source. However, I noticed there was a bug that the SOAP port (for calendar I think) was always set to 0. So here is what I did:

1. Install git (sudo apt-get install git)
2. git clone git://git.gnome.org/evolution-groupwise
3. cd evolution-groupwise
4. git checkout -b 3.2.0-patch EVOLUTION_GROUPWISE_3_2_0
5. git cherry-pick 3aae80f55d5fd565274f19210564e74d5350a66c # This is the patch for the SOAP port bug
6. Open configure.ac, at about line 48 add the line AC_CHECK_LIB(gthread-2.0, g_thread_init)
7. sudo apt-get build-dep evolution
8. ./autogen.sh
9. make
10. sudo make install
11. Edit /etc/services like bruhein describes

That's it I think

---

### Post by strakakl on 2011-11-05
Hi there,

i followed bpedmans step to compile the evolution groupwise plugin. Unfortunately at step 8 - ./autogen.sh - i got the message
```

checking for EVOLUTION_PLUGIN... no
configure: error: Package requirements (evolution-plugin-3.0 >= 3.2.0) were not met:

No package 'evolution-plugin-3.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables EVOLUTION_PLUGIN_CFLAGS
and EVOLUTION_PLUGIN_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```But in Synaptic i found that the plugins are already installed, version 3.2.0-0ubuntu2. My System is Ubuntu 11.10 64bit.

Any ideas how to solve this problem?

Cheers,
Klaus

---

### Post by bruhein on 2011-11-05
That's a bit tricky because the package has a different name.

Try to install the package "evolution-dev".

Maybe you get late the problem that there is "db.h" missing. This problem could be solved by installing the package "libdb-dev".

So try:

[FONT=Courier New]sudo apt-get install evolution-dev libdb-dev[/FONT]

---

### Post by strakakl on 2011-11-05
Hi bruhein,

thanks for your reply, i already recognized that i need to install the evolution-dev package. And your right, after that, the db.h was missing :)

Now, "make" and "sudo make install" finished without errors but in evolution i cannot select "groupwise server". That's a little bit strange, isn't it?

I will have to investigate this :(

---

### Post by bruhein on 2011-11-06
Try to reboot after "sudo make install". The evolution data server is always running even if you stop evolution itself.

---

### Post by strakakl on 2011-11-06
i tried to reboot, but that doesn't solve the problem. Starting evolution from a terminal i found

```

(evolution:2418): evolution-plugin-lib-WARNING **: can't load plugin '/usr/lib/evolution/3.2/plugins/liborg-gnome-groupwise-features': libegroupwise-1.2.so.13: cannot open shared object file: No such file or directory

(evolution:2418): evolution-plugin-lib-WARNING **: can't load plugin '/usr/lib/evolution/3.2/plugins/liborg-gnome-groupwise-features': libegroupwise-1.2.so.13: cannot open shared object file: No such file or directory

(evolution:2418): GLib-WARNING **: GError set over the top of a previous GError or uninitialized memory.
This indicates a bug in someone's code. You must ensure an error is NULL before it's set.
The overwriting error message was: No provider available for protocol 'groupwise'

(evolution:2418): evolution-mail-WARNING **: e_mail_store_add_by_account: Failed to add transport service: No provider available for protocol 'groupwise'

(evolution:2418): evolution-mail-WARNING **: Couldn't get service: klaus.straka@jku.at: Could not load /usr/lib/evolution-data-server/camel-providers/libcamelgroupwise.so: libegroupwise-1.2.so.13: cannot open shared object file: No such file or directory

(evolution:2418): camel-CRITICAL **: camel_session_add_service: assertion `uri_string != NULL' failed

(evolution:2418): evolution-plugin-lib-WARNING **: can't load plugin '/usr/lib/evolution/3.2/plugins/liborg-gnome-groupwise-features': libegroupwise-1.2.so.13: cannot open shared object file: No such file or directory

(evolution:2418): e-utils-CRITICAL **: Plugin "GroupWise Features" is missing a function named gw_ui_mail_folder_popup()

(evolution:2418): evolution-plugin-lib-WARNING **: can't load plugin '/usr/lib/evolution/3.2/plugins/liborg-gnome-groupwise-features': libegroupwise-1.2.so.13: cannot open shared object file: No such file or directory

(evolution:2418): e-utils-CRITICAL **: Plugin "GroupWise Features" is missing a function named gw_ui_mail_message_popup()


```I am not sure but i think the  libegroupwise-1.2.so.13 file results from the build process. But why is it missing? :confused:

---

### Post by bruhein on 2011-11-06
Try [FONT=Courier New]locate libegroupwise-1.2.so.13[/FONT]

There should be something like:

[FONT=Courier New]/home/bruhein/checkout/gnome/evolution/evolution-groupwise-3.2.1/src/server/.libs/libegroupwise-1.2.so.13
/home/bruhein/checkout/gnome/evolution/evolution-groupwise-3.2.1/src/server/.libs/libegroupwise-1.2.so.13.0.1
/usr/local/lib/libegroupwise-1.2.so.13
/usr/local/lib/libegroupwise-1.2.so.13.0.1
[/FONT]
Can you post yours?

---

### Post by strakakl on 2011-11-06
On my system it's


/home/**/evolution-groupwise/src/server/.libs/libegroupwise-1.2.so.13
/home/**/evolution-groupwise/src/server/.libs/libegroupwise-1.2.so.13.0.1
/usr/local/lib/libegroupwise-1.2.so.13
/usr/local/lib/libegroupwise-1.2.so.13.0.1

looks very similar to yours.

---

### Post by bruhein on 2011-11-06
The error message says:  

[FONT=Courier New]can't load plugin '/usr/lib/evolution/3.2/plugins/liborg-gnome-groupwise-features': libegroupwise-1.2.so.13: cannot open shared object file: No such file or directory[/FONT]

So your evolution expects libegroupwise-1.2.so.13 in /usr/lib/evolution/3.2/plugins

But make install puts the library in /usr/local/lib

Why don't you make a simple symbolic link from /usr/lib/evolution/3.2/plugins to /usr/local/lib? 

[FONT=Courier New]sudo ln -s /usr/local/lib/libegroupwise-1.2.so.13 /usr/lib/evolution/3.2/plugins/libegroupwise-1.2.so.13

[/FONT]Sure - a quite dirty trick and you should keep that in your mind and tidy up all that when there is a bugfix from Ubuntu.

---

### Post by strakakl on 2011-11-07
That,s it!

Thanks again for your help

---

### Post by LangTall on 2012-11-02
Just tried this on an Ubuntu 12.04 installation, does work uptill the symlinks. Even after a reboot the errormessage 'can't load plugin' as described by strakakl keeps appearing. Any idea's?

---

### Post by oldos2er on 2012-11-02
Hi LangTall, please start a new thread.

If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

