---
title: "Multi Session login with x11vnc"
date: 2010-05-31
forum: General Help
---

### Post by krunge on 2010-05-31
I'm creating a new thread based on this post by batagy:

[http://ubuntuforums.org/showpost.php?p=9373202&postcount=25](http://ubuntuforums.org/showpost.php?p=9373202&postcount=25)

> 
So I have running x11vnc as service without any problem (running on Solaris 10 and SLES10 too). I'm using the x11vnc's inbuilt "user chooser" screen (that little black screen), these command line options:

x11vnc -inetd -unixpw -users unixpw= -display WAIT:cmd=FINDCREATEDISPLAY-Xvnc.xdmcp -env X11VNC_CREATE_GEOM=1248x900 (plus a couple of other options that are not interesting here)

My question is related to the wanted VNC screen size. By default, I set the defauls screen size to 1248x900, as can be seen above.

Currently , when a user want to personalize his/her screen size to be started, he can do it this way: when the small black authentication window is appearing first, after his username, he's entering a colon, then specify the wanted resolution in this format: geom=1600x1200.

My question: is it possible somehow to set automatically the preferred screen size, without entering this ":geom=1600x1200" string in the authentication window? I mean to set it per user, without modifying the service options.
I mean, for example setting the X11VNC_CREATE_GEOM or FD_GEOM variables in the user's home ".profile" for example?


---

### Post by krunge on 2010-05-31
> 
My question: is it possible somehow to set automatically the preferred screen size, without entering this ":geom=1600x1200" string in the authentication window? I mean to set it per user, without modifying the service options.

I found a safe way to do this.  Instead of modifying x11vnc's create_display script, after the user logs successfully at the little black window x11vnc checks if the user has an option preferences file and if so appends the first line of it to the user options.  Then the sanity checking x11vnc does will apply as though the user typed it in over the network.

Here is the x11vnc "-display WAIT:..." help describing the new feature:
```

         User preferences file: Instead of having the user type
         in geom=WxH,... etc. every time he logs in to find
         or create his X session, if you set FD_USERPREFS to
         a string that does not contain the "/" character,
         then the user's home directory is prepended to that
         string and if the file exists its first line is read
         and appended to any options he supplied at the login:
         prompt.  For example -env FD_USERPREFS=.x11vnc_create
         and the user put "geom=1600x1200" in his
         ~/.x11vnc_create file.

```
So you must set -env FD_USERPREFS=... to the filename you choose to enable the feature, and then the user puts his opt string in that file.

This feature is available in the x11vnc 0.9.11 development tarball and binaries.  If you try it let me know how it went.

---

### Post by batagy on 2010-05-31
> **krunge said:**
> I found a safe way to do this.  Instead of modifying x11vnc's create_display script, after the user logs successfully at the little black window x11vnc checks if the user has an option preferences file and if so appends the first line of it to the user options.  Then the sanity checking x11vnc does will apply as though the user typed it in over the network.

Here is the x11vnc "-display WAIT:..." help describing the new feature:

...

So you must set -env FD_USERPREFS=... to the filename you choose to enable the feature, and then the user puts his opt string in that file.

This feature is available in the x11vnc 0.9.11 development tarball and binaries.  If you try it let me know how it went.

Hi Karl!

Many thanks for your fast work! That looks very promiseful! That's exactly what I imagined about it. I even noticed your new documentation regarding the new FD_USERPREFS option just before you posted this, and wanted to make feedback, but you were faster! Anyway, I'll check this (on Solaris) and I'll make a feedback for that.

Also, I want to answer for questions taken on the previous thread, so it will be answered on my next post.

---

### Post by batagy on 2010-05-31
Hi Karl,

Now to answer your previous questions, even now you implemented the solution:

First of all, just for info, the complete x11vnc arguments that I use here (obviously the IP address should be replaced with real one, and line breaks are inserted for better reading, so do not just copy and paste!):

EDIT: As krunge pointed it below, **PLEASE NOTE that use of UNIXPW_DISABLE_SSL and UNIXPW_DISABLE_LOCALHOST below in this case , makes a big security risk, as the Unix logins and passwords will be sent in CLEAR TEXT. This is normally should be avoided! Normally, do not use the "UNIXPW_DISABLE_SSL=1" and "UNIXPW_DISABLE_LOCALHOST=1" options, so the connection will be SSL secured!** END OF EDIT.

**On Solaris 10:**
```
inetadm -m network/x11vnc/tcp exec="/usr/local/bin/x11vnc -inetd 
-env UNIXPW_DISABLE_SSL=1 
-env UNIXPW_DISABLE_LOCALHOST=1 -env PATH=/usr/X11/bin:$PATH 
-env X11VNC_CREATE_GEOM=1248x900 
-unixpw -users unixpw= -display WAIT:cmd=FINDCREATEDISPLAY-Xvnc.xdmcp
-o /var/log/x11vnc.log -solid '#76848F' -nowireframe -onetile -sloppy_keys 
-listen <IP_ADDRESS> -clear_keys -skip_lockkeys 
-env FD_OPTS='-dpi 96 -from <IP_ADDRESS> -fp tcp/localhost:7100' 
-env FD_EXTRA='/usr/openwin/bin/xset -fp tcp/<IP_ADDRESS>:7100'"
```[B]

On SLES10 SP2[/B], it is a shell script:
```
#!/bin/sh
UNIXPW_DISABLE_LOCALHOST=1
export UNIXPW_DISABLE_LOCALHOST

UNIXPW_DISABLE_SSL=1
export UNIXPW_DISABLE_SSL

FD_OPTS="-dpi 96 -from <IP_ADDRESS>"
export FD_OPTS

X11VNC_CREATE_GEOM=1248x900
export X11VNC_CREATE_GEOM

/usr/local/bin/x11vnc -inetd -unixpw 
-users unixpw= -display WAIT:cmd=FINDCREATEDISPLAY-Xvnc.xdmcp 
-o /var/log/x11vnc.log -sloppy_keys -solid "#76848F" -nowireframe
 -listen <IP_ADDRESS> -clear_keys -skip_lockkeys

```Then the x11vnc xinetd conf file on the **SLES10 SP2**:
```
service x11vnc
{
    port            = 5900
    disable         = no
    socket_type     = stream
    protocol        = tcp
    wait            = no
    user            = root
    server          = /usr/local/bin/x11vnc_sh
    type            = UNLISTED
}

```Now your questions:

> **krunge said:**
> I have a couple questions.

You use Xvnc instead of Xvfb. Is that working OK? I haven't tried it in years. Does your Xvnc support RANDR? If so the user might be able to configure the desired desktop size thru his desktop GUI. Your thoughts on this?

Yes, the Xvnc is working OK both on Solaris 10 and SLES10. First I used Xvfb, but later I switched to Xvnc for 3 reasons:
- Using Xvfb on SLES10, by default, completely messed up the key codemap. The key codemap was totally different for Xvfb and Xvnc on SLES10. Using Xvfb it was not possible to enter certain keys, as the were mapped for various keyboard shortcuts to start StarOffice etc. So it was messed. Later I was able to fix the keymap by running xmodmap after login (like FD_EXTRA="xmodmap /etc/xmodmaprc"), but it was not worth it by the next two reason.
- Using Xvfb resulted a 3 button mouse (xmodmap -pp), while Xvnc resulted a 5 button mouse. And even I was able to modify it with the same method above, but the scrolling did not work with Xvfb. But the scroll works with Xvnc.
- The 3rd reason for Xvnc, that when using the "-display WAIT:cmd=FINDCREATEDISPLAY-Xvnc.xdmcp" option, the username is automatically filled at the XDMCP login screen with Xvnc. When used Xvfb, the username was not filled automatically. I mean the login screen is still there, but at all the username don't need to be entered by keyboard, it just needs an "Enter" then the password.

Otherwise, I didn't found any difference between Xvnc and Xvfb. Bot seems to be running Virtually with the same speed. I might be wrong but I experienced this.

--> Do you have any comment between the difference of Xvnc and Xvfb, when running it as service on a headless machine?

The RANDR extension is not supported, so then I guess it's not possible to resize through  desktop GUI:

**On Solaris:**
```
xdpyinfo
....
number of extensions:    25
    BIG-REQUESTS
    DAMAGE
    DEC-XTRAP
    DOUBLE-BUFFER
    Extended-Visual-Information
    MIT-SCREEN-SAVER
    MIT-SHM
    MIT-SUNDRY-NONSTANDARD
    RECORD
    RENDER
    SECURITY
    SHAPE
    SYNC
    SolarisIA
    TOG-CUP
    VNC-EXTENSION
    X-Resource
    XAccessControlExtension
    XC-APPGROUP
    XC-MISC
    XEVIE
    XFIXES
    XFree86-Bigfont
    XTEST
    XVideo

```**On SLES10:**

```
xdpyinfo
number of extensions:    25
    BIG-REQUESTS
    DAMAGE
    DEC-XTRAP
    DOUBLE-BUFFER
    Extended-Visual-Information
    GLX
    LBX
    MIT-SCREEN-SAVER
    MIT-SHM
    MIT-SUNDRY-NONSTANDARD
    RECORD
    RENDER
    SECURITY
    SGI-GLX
    SHAPE
    SYNC
    TOG-CUP
    VNC
    X-Resource
    XC-APPGROUP
    XC-MISC
    XFIXES
    XFree86-Bigfont
    XTEST
    XVideo

```> **krunge said:**
> I see you are also using 'xdmcp'. Presumably the user is supplying his password twice for the first connection? (i.e once at the little black screen and 2nd at the gdm/kdm/xdm login screen)

Yes, I use xdmcp option. Yes they are entering password twice in the first time. Before, I didn't know there is a method to eliminate the second login screen step. Now, you triggered me, I just tried **"-env FD_SESS=gnome" and remove the ".xdmcp" option**. It is working and it eliminates the second step!! Very good! But as for now, somehow it is not fully correct. $USER variable is missing and some is missing from $PATH, and there are some font issues in this way for me. Also there are some errors in the x11vnc log when using "-env FD_SESS=gnome" and without the xdmcp, so I don't know why it is not fully compatible with the .xdmcp method.....
---> Do you have any comment on this?

Thanks for all your help!

---

### Post by krunge on 2010-05-31
> **batagy said:**
> 
Many thanks for your fast work! That looks very promiseful! That's exactly what I imagined about it. I even noticed your new documentation regarding the new FD_USERPREFS option just before you posted this, and wanted to make feedback, but you were faster! Anyway, I'll check this (on Solaris) and I'll make a feedback for that.

Yes, thanks for bringing it up.  I always felt a little embarassed about the user interface for the extended "login:" prompt because they had to type it in every time.  I didn't want to make a GUI out of VNC primitives... your  per-user preferences file idea is a good compromise and perhaps closer to what people want.

---

### Post by krunge on 2010-05-31
batagy,

I'm sure you understand exactly what you are doing, but for the benefit of others who might not think before they cut-and-paste, I want to point out that your use of UNIXPW_DISABLE_SSL and UNIXPW_DISABLE_LOCALHOST means that the Unix usernames and **passwords** are sent in **CLEAR TEXT** across the network.

That is to say, the way you are using it anyone sniffing the network can obtain unix usernames and passwords and hence be able to log in as those users, either via your VNC setup or SSH, etc.  So it is basically as unsafe as telnet.

I understand this is acceptable in some work environments, but I hope it is clear to those reading this thread that the unix passwords are sent in clear text and so it is a very risky way to operate.

---

### Post by batagy on 2010-06-07
> **krunge said:**
> So you must set -env FD_USERPREFS=... to the filename you choose to enable the feature, and then the user puts his opt string in that file.

This feature is available in the x11vnc 0.9.11 development tarball and binaries.  If you try it let me know how it went.

> **krunge said:**
> Yes, thanks for bringing it up.  I always felt a little embarassed about the user interface for the extended "login:" prompt because they had to type it in every time.  I didn't want to make a GUI out of VNC primitives... your  per-user preferences file idea is a good compromise and perhaps closer to what people want.

Hi Karl,

Sorry for late answer.
I tried this feature with the Linux build on VirtualBox, and it works perfectly!
This is a good and useful feature indeed!

Thanks a lot again for your fast work!

---

### Post by batagy on 2010-06-15
Hi Karl,

Maybe could you make a new Solaris Sparc 64bit build also from this new beta?

Thanks
György

---

### Post by batagy on 2010-06-28
Hi Karl,

May I have another question. It's unrelated to the above feature.

What does the "client 1 network rate 166.3 KB/sec (19587.6 eff KB/sec)" message in the x11vnc log mean exactly? And which is better, if the value bigger or smaller?
I find this "client 1 network rate" value to be different for different VNC clients.

Logs (only end section of the x11vnc log):

**In case of TigerVNC:**
```
24/06/2010 17:55:09 Battling with something for -norepeat!! (1 resets left)
24/06/2010 17:55:09 Disabled X server key autorepeat.
24/06/2010 17:55:09   to force back on run: 'xset r on' (2 times)
24/06/2010 17:55:09 created   xdamage object: 0xa00007
24/06/2010 17:55:09 Sending rfbEncodingNewFBSize for resize to (1248x900)
**24/06/2010 17:55:09 client 1 network rate 166.3 KB/sec (19587.6 eff KB/sec)**
24/06/2010 17:55:09 client 1 latency:  2.0 ms
24/06/2010 17:55:09 dt1: 0.0510, dt2: 0.0334 dt3: 0.0020 bytes: 13862
24/06/2010 17:55:09 link_rate: LR_UNKNOWN - 1 ms, 166 KB/s
24/06/2010 17:55:09 copy_tiles: allocating first_line at size 40
24/06/2010 17:55:17 Battling with something for -norepeat!! (0 resets left)
24/06/2010 17:55:17 Disabled X server key autorepeat.
24/06/2010 17:55:17   to force back on run: 'xset r on' (1 times)
24/06/2010 17:55:23 created selwin: 0xa00008
24/06/2010 17:55:23 called initialize_xfixes()

```


**In case of TurboVNC:**

```
24/06/2010 18:01:31 Battling with something for -norepeat!! (1 resets left)
24/06/2010 18:01:31 Disabled X server key autorepeat.
24/06/2010 18:01:31   to force back on run: 'xset r on' (2 times)
24/06/2010 18:01:31 created   xdamage object: 0xa00007
24/06/2010 18:01:32 copy_tiles: allocating first_line at size 40
24/06/2010 18:01:32 Sending rfbEncodingNewFBSize for resize to (1248x900)
**24/06/2010 18:01:32 client 1 network rate 2095.0 KB/sec (20494.6 eff KB/sec)**
24/06/2010 18:01:32 client 1 latency:  1.7 ms
24/06/2010 18:01:32 dt1: 0.0752, dt2: 0.0358 dt3: 0.0017 bytes: 230751
24/06/2010 18:01:32 link_rate: LR_LAN - 1 ms, 2095 KB/s
24/06/2010 18:01:39 Battling with something for -norepeat!! (0 resets left)
24/06/2010 18:01:39 Disabled X server key autorepeat.
24/06/2010 18:01:39   to force back on run: 'xset r on' (1 times)
24/06/2010 18:01:45 created selwin: 0xa00008
24/06/2010 18:01:45 called initialize_xfixes()

```


**In case of TightVNC:**
```
24/06/2010 18:09:13 Battling with something for -norepeat!! (1 resets left)
24/06/2010 18:09:13 Disabled X server key autorepeat.
24/06/2010 18:09:13   to force back on run: 'xset r on' (2 times)
24/06/2010 18:09:13 created   xdamage object: 0xa00007
24/06/2010 18:09:13 Sending rfbEncodingNewFBSize for resize to (1248x900)
**24/06/2010 18:09:15 client 1 network rate 9.4 KB/sec (1108.0 eff KB/sec)**
24/06/2010 18:09:15 client 1 latency:  3.0 ms
24/06/2010 18:09:15 dt1: 0.0600, dt2: 1.4153 dt3: 0.0030 bytes: 13860
24/06/2010 18:09:15 link_rate: LR_DIALUP - 2 ms, 9 KB/s
24/06/2010 18:09:15 copy_tiles: allocating first_line at size 40
24/06/2010 18:09:23 Battling with something for -norepeat!! (0 resets left)
24/06/2010 18:09:23 Disabled X server key autorepeat.
24/06/2010 18:09:23   to force back on run: 'xset r on' (1 times)
24/06/2010 18:09:27 created selwin: 0xa00008
24/06/2010 18:09:27 called initialize_xfixes()

```

So the **client 1 network rate **seems to be varies for various VNC clients. Which is the better one? What is means?

Thanks
György

---

### Post by krunge on 2010-06-28
> **batagy said:**
> 
So the **client 1 network rate **seems to be varies for various VNC clients. Which is the better one? What is means?

Hi,

I'm sorry that those network rates can be distracting and misleading.

x11vnc tries to estimate certain connection rates & etc.  Network latency and bandwidth are estimated to the vnc client; and also the (local) framebuffer read-rate (this can often be so slow as to be the bottleneck.)

I call these 'distracting' because x11vnc doesn't do much with the information.  As an example, based on what it finds for the latency and bandwidth it might increase some heuristic timeout values for the automatic wireframe and scroll detection.  It really doesn't do much more than that (currently and perhaps forever.)

In no case does x11vnc make a decision on which VNC encoding to use based on these estimates.  Encoding selection is the job of the VNC client, not the VNC server (and the client, too, may try to estimate bandwidth and latency to try to decide.)

It turns out that x11vnc has a rather difficult time estimating the bandwidth, it is usually true for the 'tight' encoding (which often sends changes in many small updates.)  I think this is what you are seeing for the slowest one (and you may find this number fluctuations a lot.)

Anyway, I don't think you should worry about what you are seeing.  I have x11vnc print them out in case they might help me deduce a problem a user has reported to me.

---

### Post by batagy on 2010-06-30
> **krunge said:**
> Hi,

I'm sorry that those network rates can be distracting and misleading.

x11vnc tries to estimate certain connection rates & etc.  Network latency and bandwidth are estimated to the vnc client; and also the (local) framebuffer read-rate (this can often be so slow as to be the bottleneck.)

I call these 'distracting' because x11vnc doesn't do much with the information.  As an example, based on what it finds for the latency and bandwidth it might increase some heuristic timeout values for the automatic wireframe and scroll detection.  It really doesn't do much more than that (currently and perhaps forever.)

In no case does x11vnc make a decision on which VNC encoding to use based on these estimates.  Encoding selection is the job of the VNC client, not the VNC server (and the client, too, may try to estimate bandwidth and latency to try to decide.)

It turns out that x11vnc has a rather difficult time estimating the bandwidth, it is usually true for the 'tight' encoding (which often sends changes in many small updates.)  I think this is what you are seeing for the slowest one (and you may find this number fluctuations a lot.)

Anyway, I don't think you should worry about what you are seeing.  I have x11vnc print them out in case they might help me deduce a problem a user has reported to me.

Hi,

Thanks for your answer. Maybe I put my question in wrong way..... Of course I understand that it's the client's task to choose the encoding and decisions.

In my previous question, I was meaning to just briefly know whether this client rate is how related to the client? I mean, it's basicly related to the encoding choosed by the client?
Because the reported client rates varies heavily for the different clients. E.g for TurboVNC 2Mbyte/sec, but for TightVNC it is only 9 kbyte/sec. So it's very big difference. Is that difference comes from the difference encoding of the client?

And, most importantly, this client rate is somehow related to the real bandwith usage on the network? Because if it is, then TurboVNC uses 2 Mbyte/sec link for the vnc server? Must be very big occupation, if that's the case.

So basicly my point is to check which client could be the best choose, and I thought this client rate printed by x11vnc, is somehow an information about bandwidth..... (?) 

Thanks
György

---

### Post by krunge on 2010-06-30
I believe I understand your question better now.

These numbers are x11vnc's **estimates** of the wire-speed to the client. As I said before x11vnc often has a difficult time estimating them, so the values should not be taken too seriously, especially if there is evidence to the contrary (e.g. good response with the viewer.)

x11vnc tries to estimate these at the very beginning, preferably when the client downloads the initial full screen.  If it is a big chunk of data then one expects the estimate to be more accurate.  So there is not a problem with the viewer if the rate appears "large", x11vnc is trying to measure the instantaneous maximum wire rate, not an average session rate. 

In fact your TightVNC estimate being small (9KB/sec) is probably due to an inaccurate measurement.  Look here at the additional info line:
```

dt1: 0.0600, dt2: 1.4153 dt3: 0.0030 bytes: 13860

```
There were 3 timing phases measured and one of them took 1.4 secs.  This is probably bogus; a delay for some other reason (e.g. unexpected pause.)  Also look that only 13860 bytes were transferred (13860 / 1.4 is the rate.)  That is definitely not the full screen, just one small part of it.  So it is an inaccurate measurement of the wire speed is all.

OTOH, look at TurboVNC.  Its chunk is 230751 bytes, and nothing looks bad about the times, so that is likely a better estimate of the wire speed (but still may be too low, I'm not sure)

Anyway, don't take these numbers too seriously.  You can do your own measurements, etc. and they will be much more reliable.

---

### Post by batagy on 2010-07-01
OK! Thanks a lot for your nice clarifications!

---

### Post by dkho on 2011-04-02
Hi, I'm having a problem with the FD_USERPREFS setting.

Now I'm trying this at the command line before porting over to inetd:
x11vnc -o /var/log/x11vnc.log -env FD_SESS=gnome -env  FD_PROG=/usr/bin/gnome-session -env FD_XSRV=/usr/X11/bin/Xserver -env  FD_USERPREFS=.x11vnc_prefs -auth ~/.Xauthority -ssl SAVE-servername  -unixpw -users unixpw= -display WAIT:cmd=FINDCREATEDISPLAY-Xvfb

I have the following line inside /export/home/user.name/.x11vnc_prefs
geom=1600x900x32

However, I never saw the screen resolution change to 1600x900 at the client side. It returns back to 1280x1024.

I get the following messages at the log (clipped to show only messages of interest):
02/04/2011 21:28:33 unixpw_verify: 'daniel-kho'
02/04/2011 21:28:33 su_verify: 'daniel-kho' for login.
02/04/2011 21:28:34 unixpw_verify: su_verify login for 'daniel-kho' succeeded.
02/04/2011 21:28:34 apply_opts: set unixname to: daniel-kho
02/04/2011 21:28:34 read user prefs /export/home/daniel.kho/.x11vnc_prefs: geom=1600x900x32
02/04/2011 21:28:34 wait_for_client: unixpw finished.
02/04/2011 21:28:34 client_set_net: <ip-address>  0.0006
02/04/2011 21:28:34 set create display geom: 1600x900x32
02/04/2011 21:28:34 wait_for_client: running: env X11VNC_SKIP_DISPLAY=''  /bin/sh /tmp/x11vnc-find_display.0la4NH
02/04/2011 21:28:34 su_verify: 'daniel-kho' for command.
02/04/2011 21:28:36 unixpw_accept failed to switch to user: daniel-kho (drc)
02/04/2011 21:28:38 Using X display :20.0
02/04/2011 21:28:38 rootwin: 0x3f reswin: 0x1600001 dpy: 0x86a7498
...
...
02/04/2011 21:28:38 Sending rfbEncodingNewFBSize for resize to (1280x1024)
02/04/2011 21:28:38 Battling with something for -norepeat!! (1 resets left)
02/04/2011 21:28:38 Disabled X server key autorepeat.


Also, another issue (probably unrelated to FD_USERPREFS). I found out I  have to use the -shared option for a multi-user, multi-session  environment? But when using -shared, I found that both all users will  log into the same X session. How do I make each user to create their own  Xsession? Anything to do with setting Xauthority? I can't seem to get  this right after trying for a long time.

Regards,
Dan

---

### Post by dkho on 2011-04-02
One thing I noticed is the -geometry setting at the server side works. However, putting "geom=1600x900x32" with the file associated with FD_USERPREFS didn't work. I tried manually appending that string at the login prompt (username:geom=1600x900x32), but this didn't change the screen size correctly as well.

For me, only -geometry works. But this will make the setting apply to all my clients (which isn't what I want).

Any thoughts or useful links to direct me to?

---

### Post by dkho on 2011-04-02
Hi Karl, I noticed something interesting in your documentation for unixpw:
A familiar "login:" and "Password:" dialog is presented to the user on a black screen inside the vncviewer.  The connection is dropped if the user fails to supply the correct password in 3 tries or does not send one before a 45 second timeout.  Existing clients are view-only during this period.This was exactly what I experienced. An existing logged-in user session will see the black login prompt when another user is attempting to connect and log in to the x11vnc server.
Also, the new user trying to log into his own unix account will actually load the existing user's Xsession, instead of creating/loading his own.

Is there a way to make existing users not see a black login screen whenever a new user tries to connect and login? Also, how do I create multiple X sessions for multiple users trying to connect? I want different users to connect to their own sessions, instead of attach to another user's X session. Of course, if that user already has his own session running, he can attach to his own session, but not to another user's session.

Please help, thanks!

Regards,
Daniel

---

### Post by dkho on 2011-04-02
Hi Karl, I noticed something interesting in your documentation for unixpw:
"A familiar "login:" and "Password:" dialog is presented to the user on a black screen inside the vncviewer.  The connection is dropped if the user fails to supply the correct password in 3 tries or does not send one before a 45 second timeout.  Existing clients are view-only during this period."

This was exactly what I experienced. An existing logged-in user session  will see the black login prompt when another user is attempting to  connect and log in to the x11vnc server.
Also, the new user trying to log into his own unix account will actually  load the existing user's Xsession, instead of creating/loading his own.

Is there a way to make existing users not see a black login screen  whenever a new user tries to connect and login? Also, how do I create  multiple X sessions for multiple users trying to connect? I want  different users to connect to their own sessions, instead of attach to  another user's X session. Of course, if that user already has his own  session running, he can attach to his own session, but not to another  user's session.

Please help, thanks!

Regards,
Daniel

---

