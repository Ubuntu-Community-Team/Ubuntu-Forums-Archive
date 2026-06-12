---
title: "Pam auth error when logon through VNC"
date: 2010-05-30
forum: General Help
---

### Post by josho133 on 2010-05-30
Hello,

On Ubuntu 10.04 with x11Vnc server, if the screen requires logon (such as if locked or upon reboot), through the VNC terminal, I always get authentication error (incorrect password). Sitting at the keyboard, I can logon just fine. Once logged on, I can access everything through VNC just fine. 

Error in auth.log (username = bob):
unix_chkpwd[3926]: password check failed for user (bob)
gnome-screensaver-dialog: pam_unix(gnome-screensaver:auth): authentication failure; logname= uid=1000 euid=1000
 tty=:0.0 ruser= rhost=  user=bob
gnome-screensaver-dialog: pam_winbind(gnome-screensaver:auth): getting password (0x00000388)
gnome-screensaver-dialog: pam_winbind(gnome-screensaver:auth): pam_get_item returned a password
gnome-screensaver-dialog: pam_winbind(gnome-screensaver:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR,
 PAM error: PAM_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user

I've tried enabling the remote desktop feature through System->Preferences, but that didn't help.
I've also tried removing my gnome keyring (rm ~/.gnome2/keyrings/*), but that didn't help.

Any idea?

---

### Post by krunge on 2010-05-30
You can run x11vnc with the "-dk" (-debug_keyboard) option and it will print every character it receives and tries to inject into the X server.  So you can at least see if it matches what you expect.

Edit: Oh, "no such user", hmmm, I'm not sure.

---

### Post by josho133 on 2010-05-30
Hi,

I've used that and the "Leave Message" feature to ensure that the text is going through perfectly. It is. The problem is how PAM is authenticating me through VNC. 
(The No Such User error).

I have no idea how to configure PAM correctly here. I've tried disabling WinBind support via pam-auth-update, but that didn't help.

> **krunge said:**
> You can run x11vnc with the "-dk" (-debug_keyboard) option and it will print every character it receives and tries to inject into the X server.  So you can at least see if it matches what you expect.

Edit: Oh, "no such user", hmmm, I'm not sure.

---

### Post by josho133 on 2010-05-30
Update: I fixed this by commenting out the following line in /etc/pam.d/common-auth:

auth   requisite                       pam_deny.so

I don't know much about PAM configs -- this doesn't seem like the correct fix. Does anyone know what the "proper" fix should be here?

Edit: This obviously isn't right (changed it back to uncommented); but it's clearly a PAM related issue.

---

### Post by krunge on 2010-05-30
Is this some sort of Windows NT Logon/Auth?

---

### Post by josho133 on 2010-05-30
Negative.

In fact, I didn't even know PAM was using WinBind for anything. I suppose because I use SAMBA it was enabled.

However, I ran pam-auth-update and disabled it. 

So, here's what my /etc/pam.d/common-auth file looks like:
auth	[success=1 default=ignore]	pam_unix.so nullok_secure
auth	requisite			pam_deny.so
auth	required			pam_permit.so

Now, the error I get is (/var/log/auth.log for user bob):
May 30 12:07:28 vmhost unix_chkpwd[3105]: password check failed for user (bob)
May 30 12:07:28 vmhost gnome-screensaver-dialog: pam_unix(gnome-screensaver:auth): authentication failure; logname= uid=1000 euid=1000 tty=:0.0 ruser= rhost=  user=bob



> **krunge said:**
> Is this some sort of Windows NT Logon/Auth?

---

### Post by josho133 on 2010-05-30
Also, in case it's relevant, here are the args for x11vnc:

/usr/bin/x11vnc -forever -display :0 -rfbauth /home/bob/.vnc/passwd -auth /var/lib/gdm/:0.Xauth &

---

### Post by krunge on 2010-05-30
Can you increase the verbosity of the pam output to actually show the password it was trying?  That would be a very useful test.

I assume x11vnc with -dk shows the correct password being injected.

Do you see "*" or something like that being entered into the password field as you type the password?

---

### Post by josho133 on 2010-05-30
Hi,

Thanks for the suggestion. I looked around but can't find anything helpful -- how does one increase the verbosity of PAM logging?

re: correct password: Yes, 100%. It is absolutely not a caps-lock, content-type, language or other textual mismatch of any kind. No "*". Password is 10 characters long, if that matters.

> **krunge said:**
> Can you increase the verbosity of the pam output to actually show the password it was trying?  That would be a very useful test.

I assume x11vnc with -dk shows the correct password being injected.

Do you see "*" or something like that being entered into the password field as you type the password?

---

### Post by krunge on 2010-05-31
If you can't find anything to increase the PAM logging (to print the password tried) you might be able to (as root) ltrace the gnome-screensaver program and watch it calling the pam interfaces. Maybe you will see the password go by.

What happens if the password length is 8?

---

### Post by krunge on 2010-05-31
> 
No "*"
For gnome-screensaver I see a dot appear in the password field when I type a character.  I believe something similar also appears in the field when I log in via the GDM greeter (don't have time to check.)

So are you not seeing a dot (or whatever) symbol appearing in the password field when you type a character but you know you would see them if you were not going through VNC? This would be an important clue--suggesting the login program does not accept artificially injected keystrokes (as x11vnc must generate.)

One other thing, I once recall someone having trouble with SELINUX security enabled.  Make sure that isn't it.

---

### Post by MrGrey1 on 2010-06-14
Hi guys,
I have the same issue as josho133. Login screen through VNC refuses to take the password, authentication failure, using x11vnc on a fresh install of 10.04.

If I go to the vnc server desktop I can log in there and everything works fine. The vnc session to the client maintains connection and I have control as per normal when I go back to the client. The asterisk marks in the password box all show up as they should when entering the password. 

This is the process taken for my setup:

1. Disable Desktop Sharing under System -> Preferences -> Remote Desktop
2. sudo apt-get install x11vnc
3. sudo x11vnc -storepasswd yourpasswordhere /home/USER/.x11vnc.pass
4. sudo gedit /etc/gdm/Init/Default
5. add this line to the bottom above exit: /usr/bin/x11vnc -rfbauth /home/USER/.x11vnc.pass -o /tmp/x11vnc.log -forever -localhost -bg -rfbport 5900
6. sudo gedit /etc/gdm/custom.conf and add KillInitClients=false under section [daemon]
7. restart

It may help to know that there were 3 other steps I used to have to do in Hardy to get this to work:

  * Go to System -> Administration -> Login Window (General tab) and uncheck "Disable multiple logins for a single user."
    * Go to the Remote tab. Change Style: to "Same as Local"
    * then click "Configure XDMCP," then uncheck "Honor indirect requests."

I can't remember, (didn't take notes) on how I did this setup on  Jaunty or Karmic. I know the GUI Login Window options were removed then and it required another step, much to my irritation.
I think it's something to do with XDMCP but having a hard time figuring out what's happened to XDMCP on 10.04. It's been turned of by default from what I can gather... 
Just my noob guessing anyway. Will post back if I find an answer.

x11vnc log:

14/06/2010 13:11:16 Client Protocol Version 3.8
14/06/2010 13:11:16 Protocol version sent 3.8, using 3.8
14/06/2010 13:11:16 rfbProcessClientSecurityType: executing handler for type 2
14/06/2010 13:11:17 created   xdamage object: 0x200041
14/06/2010 13:11:18 authProcessClientMessage: authentication failed from 127.0.0.1
14/06/2010 13:11:18 rfbAuthProcessClientMessage: password check failed
14/06/2010 13:11:18 rfbClientSendString("password check failed!")
14/06/2010 13:11:18 client_count: 0
14/06/2010 13:11:18 Restored X server key autorepeat to: 1

Looks like this bug is the same problem:
[https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/587743](https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/587743)

---

### Post by krunge on 2010-06-14
> **MrGrey1 said:**
> 
14/06/2010 13:11:16 Client Protocol Version 3.8
14/06/2010 13:11:16 Protocol version sent 3.8, using 3.8
14/06/2010 13:11:16 rfbProcessClientSecurityType: executing handler for type 2
14/06/2010 13:11:17 created   xdamage object: 0x200041
14/06/2010 13:11:18 authProcessClientMessage: authentication failed from 127.0.0.1
14/06/2010 13:11:18 rfbAuthProcessClientMessage: password check failed
14/06/2010 13:11:18 rfbClientSendString("password check failed!")
14/06/2010 13:11:18 client_count: 0
14/06/2010 13:11:18 Restored X server key autorepeat to: 1

Looks like this bug is the same problem:
[https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/587743](https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/587743)
No, this looks like a different problem.  Your above log indicates the VNC password login failed, not at the GNOME unix user login panel as that bugreport or the OP has.

The error above comes when you type in the VNC password incorrectly. Maybe recreate the VNC passwd (rfbauth) file again.  You probably should not use more than 8 characters (although I think the vnc apps automatically drop the extra characters).

---

### Post by MrGrey1 on 2010-06-16
> **krunge said:**
> No, this looks like a different problem.  Your above log indicates the VNC password login failed, not at the GNOME unix user login panel as that bugreport or the OP has.

The error above comes when you type in the VNC password incorrectly. Maybe recreate the VNC passwd (rfbauth) file again.  You probably should not use more than 8 characters (although I think the vnc apps automatically drop the extra characters).

Hey krunge, thanks for your input.
That's interesting. The VNC connection actually works. I can see the desktop login screen and if I login on the vnc server mouse/KB then I have full VNC access from the client machine without the connection dropping. For all intents and purposes the VNC password 'works.' I have a simple 7 character password for the VNC. I'll try resetting the PW and see what happens.


EDIT: I've done some further testing, I reset the vnc passwd. I then successfully logged into the server when the server was already at the desktop. I then disconnected vnc logged the server out of desktop and logged back in with vnc. I could control the mouse and access and modify all the extra options on the server login screen, (change keyboard, accessibility etc.) 
I could not however enter the password without getting an authentication failure message. 
Just per chance I tried the onscreen keyboard option and was able to login successfully!!! So not a fix but a work around for me that's not to inconvenient.
I tested all the characters on the keyboard in notepad while logged in via vnc and they all displayed properly.
I also tried both US and UK keymaps at the login screen without success.
VNC is definitely accepting it's password as I have full control of the desktop and the login screen. The only thing that I can't do is login to the desktop... Weird...?


PS. sorry I didn't mean to hijack this thread. I thought it was the same issue...

---

### Post by AlwaysLearning on 2010-07-19
Hi guys,

I upgraded from Karmic to Lucid over the weekend and ran into this same problem of PAM authentication from the Greeter screen via x11vnc...

My VNC password worked to connect to the machine, as always, but whenever I typed my password into the Greeter screen I got "Authentication failure" after a couple of seconds. I added the "-kd" option to x11vnc in /etc/gdm/Init/Default, restarted the machine and tried again. Still the same issue, and I could see that the correct keycodes were being received in the /var/log/x11vnc.log file:

19/07/2010 13:43:31 # keyboard(up, 0xffe9 "Alt_L") uip=0  304.7915
19/07/2010 13:43:31 # keyboard(up, 0xffe3 "Control_L") uip=0  304.7917
19/07/2010 13:43:31 # keyboard(up, 0xffe1 "Shift_L") uip=0  304.7918
19/07/2010 13:43:31 # keyboard(up, 0xffea "Alt_R") uip=0  304.7920
19/07/2010 13:43:31 # keyboard(up, 0xffe4 "Control_R") uip=0  304.7921
19/07/2010 13:43:31 # keyboard(up, 0xffe2 "Shift_R") uip=0  304.7923
19/07/2010 13:43:34 # keyboard(down, 0xffe1 "Shift_L") uip=0  307.6056
19/07/2010 13:43:34 # keyboard(down, 0x.. ".") uip=0  307.7966
19/07/2010 13:43:34 # keyboard(up, 0x.. ".") uip=0  307.8904
19/07/2010 13:43:34 # keyboard(up, 0xffe1 "Shift_L") uip=0  308.0004
19/07/2010 13:43:35 # keyboard(down, 0x.. ".") uip=0  308.1142
19/07/2010 13:43:35 # keyboard(up, 0x.. ".") uip=0  308.1935
19/07/2010 13:43:35 # keyboard(down, 0x.. ".") uip=0  308.3531
19/07/2010 13:43:35 # keyboard(up, 0x.. ".") uip=0  308.4318
19/07/2010 13:43:35 # keyboard(down, 0x.. ".") uip=0  308.5284
19/07/2010 13:43:35 # keyboard(up, 0x.. ".") uip=0  308.6271
19/07/2010 13:43:35 # keyboard(down, 0x.. ".") uip=0  308.6879
19/07/2010 13:43:35 # keyboard(up, 0x.. ".") uip=0  308.7686
19/07/2010 13:43:35 # keyboard(down, 0xffe1 "Shift_L") uip=0  308.9755
19/07/2010 13:43:36 # keyboard(down, 0x.. ".") uip=0  309.1378
19/07/2010 13:43:36 # keyboard(up, 0xffe1 "Shift_L") uip=0  309.2378
19/07/2010 13:43:36 # keyboard(up, 0x.. ".") uip=0  309.2473
19/07/2010 13:43:36 # keyboard(down, 0x.. ".") uip=0  309.4126
19/07/2010 13:43:36 # keyboard(up, 0x.. ".") uip=0  309.4752
19/07/2010 13:43:36 # keyboard(down, 0x.. ".") uip=0  309.5218
19/07/2010 13:43:36 # keyboard(up, 0x.. ".") uip=0  309.6048
19/07/2010 13:43:36 # keyboard(down, 0x.. ".") uip=0  309.7281
19/07/2010 13:43:36 # keyboard(up, 0x.. ".") uip=0  309.8088
19/07/2010 13:43:36 # keyboard(down, 0x.. ".") uip=0  309.8561
19/07/2010 13:43:36 # keyboard(up, 0x.. ".") uip=0  309.9240

One thing I thought was interesting was the second shifted character - the Shift-up was logged before the key release, which I didn't think was the case, so I sudo passwd'd my password to all lowercase, restarted the machine and tried again. (Thank goodness for SSH.)

This time I was able to login successfully. So, tempting fate, I changed my password to mixed case and tried again... and was able to login again.

Is it possible that there's a PAM Version Number (or something) stored with the password and this needed to be updated since the Karmic-Lucid upgrade?

The other thing I've noticed, and this is a security issue IMO, is that the neither the Greeter's password nor the Change Password function (in Preferences/About Me) is case sensitive any more. I can now authenticate with all lowercase characters even though my password was set with mixed case. Need to go hunting for options controlling that behaviour now. :(

---

### Post by AlwaysLearning on 2010-07-20
This part is still relevant, by the way, but only remotely...
> **AlwaysLearning said:**
> 
The other thing I've noticed, and this is a security issue IMO, is that the neither the Greeter's password nor the Change Password function (in Preferences/About Me) is case sensitive any more. I can now authenticate with all lowercase characters even though my password was set with mixed case. Need to go hunting for options controlling that behaviour now. :(

There is definitely something weird going on here. When I got home last night I experimented at the local console. Passwords were indeed case-sensitive in Preferences/About Me, the Greeter screen and also the Unlock (from screensaver) screen.

Today, however, when connecting from work via TightVNC and x11vnc I could not login - same Authentication failure. Via the SSH window I issued "sudo passwd username" and changed the password to "passpass" (all lower case). I could now login from the Greeter screen or the Unlock screen using "PASSPASS" or "passpass" or any combination of uppercase or lowercase letters such as "pASSpASS".

I'll do some more testing from TightVNC and UltraVNC on another machine when I get home tonight, but there's definitely something strange going on with passwords over VNC at the moment. I double-checked in Synaptic and I have x11vnc 0.9.9-1 installed.

---

### Post by croemmich on 2010-07-21
I was seeing the same issues as AlwaysLearning, however I added the **-xkb** flag and it seems to have taken care of it. Here is my command:

[/etc/gdm/Init/Default]
/usr/bin/x11vnc-0.9.10 -localhost -o /tmp/x11vnc.log -noxdamage -xkb -bg -rfbauth /etc/.vncpasswd -rfbport 5900

---

### Post by AlwaysLearning on 2010-07-24
I finally got back to this today (too many family things the last few days)...

Even though the x11vnc server was logging shift-up and shift-down key events it seems as though it was having problems passing them through to the Gnome session. I verified this coming in via TightVNC, opening gedit and typing "The Quick Brown Fox jumped over the Lazy Dog." but it came out "the quick brown fox jumped over the lazy dog."

The reasons I saw what I saw a few days ago were:
1. My first password change was via SSH and was set to all lower-case letters, so I was able to login via VNC.
2. My second password change was via About Me/Change Password when using VNC, so all the uppercase characters I typed in were received by Gnome as lowercase. This also explains why all variations of "PASSPASS" were accepted at the Greeter and Unlock screens over VNC - they were all being received by Gnome as lowercase as well.
3. My third password change was via About Me/Change Password at the local console when I got home that night. That was a mixed-case password and explains why I couldn't login again the next day - the Gnome session was only seeing lowercase characters.

As croemmich did a couple of days ago, I added the -xkb switch to the x11vnc start line and now uppercase characters are working as expected over VNC.

[/etc/gdm/Init/Default]
/usr/bin/x11vnc -bg -forever --localhost -o /var/log/x11vnc.log -rfbauth /etc/x11vnc.passwd -rfbport 5900 -xkb

---

### Post by krunge on 2010-07-24
> I added the **-xkb** flag and it seems to have taken care of it. Here is my command:

[/etc/gdm/Init/Default]
/usr/bin/x11vnc-0.9.10 -localhost -o /tmp/x11vnc.log -noxdamage -xkb -bg -rfbauth /etc/.vncpasswd -rfbport 5900
The 0.9.11 development version of x11vnc enables -xkb by default. If you are willing to try it out in your environment (not supplying -xkb) and report back here if it worked or not that would be much appreciated.

---

### Post by AlwaysLearning on 2010-07-24
I downloaded x1vnc-0.9.11 from [http://www.karlrunge.com/x11vnc/](http://www.karlrunge.com/x11vnc/)

I can confirm that it handles shifted characters correctly without -xkb.

[/etc/gdm/Init/Default]
/usr/bin/x11vnc-0.9.11 -bg -forever -localhost -o /var/log/x11vnc.log -rfbauth /etc/x11vnc.passwd -rfbport 5900

---

### Post by krunge on 2010-07-25
> **AlwaysLearning said:**
> I downloaded x1vnc-0.9.11 from [http://www.karlrunge.com/x11vnc/](http://www.karlrunge.com/x11vnc/)

I can confirm that it handles shifted characters correctly without -xkb.

Great.  Thanks for verifying this is fixed.

---

