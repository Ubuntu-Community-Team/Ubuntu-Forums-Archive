---
title: "unable to login"
date: 2010-05-04
forum: General Help
---

### Post by Menyus on 2010-05-04
I have an HP dv9000 17" laptop, dual boot Win7/Ubuntu 10.04 LTS 64-bit, 512MB nVidia GeForce 8600M GS. Until the last reboot everything worked perfectly, but now, I am unable to get past the graphical login screen. I click on my username, type in my password, the screen flashes a few times and redisplays the login screen. I can go through this process as many times as I wan to. The system doesn't hang but I am unable to login. (Note: I can login using CTRL+ALT+F1.) As far as I now, nothing changed between logins. I only switched into Windows for a short time to use a WIndows app. I suspect the nvidia driver may be causing the problem. So how do I fix this? Please, help. Thanks.

---

### Post by sunk8 on 2010-05-04
Do you get any error messages there?
):P
Like 'Authentication Failure' perhaps?

---

### Post by WorMzy on 2010-05-04
Go to a tty (Ctrl+Alt+F1) and log in, then try running 'startx'. Does it cause the same behaviour?

If so, also in a tty, run 'sudo apt-get purge nvidia-*' and then 'startx' again.

---

### Post by Menyus on 2010-05-05
Thanks for the replies. 

After login with CTRL-ALT-F1, startx gives Fatal error because there is already an xserver running on terminal 0. 

Purging the nvidia driver seemed to work but I still have the same exact problem; that is, after entering my username and password, I cannot get past the graphical login screen. 

Unfortunately, there is no visible error messages.

Anymore ideas? Thanks.

---

### Post by WorMzy on 2010-05-05
Sorry, I should have told you to run 'sudo pkill gdm' before you tried 'startx'. Try it again, and see if it shows any errors.

---

### Post by Menyus on 2010-05-05
Thanks again for the suggestions. I am no able to log into my system and use it but not without any hassle. This is what I have to do to be able to use my system:

1. CTRL-ALT-F1 at the login screen to login at the command line.

2. Establish path: PATH="..."

3. Find the PID for the running gdm: 

  $ pgrep -u root gdm

(Note: on my system, there is no pkill and I coulnd't install it either.)

4. Kill the gdm process:

  $ sudo kill -TERM pid_of_gdm

5. Get X started:

  $ startx

6. After X starts, I get an "Unlock Login Keyring" dialog box where I have to enter my password.

After all this, the system seems to be running OK but this is going to be a huge pain to have to go through this at every reboot!!! Any ideas how I can fix this? Thanks.

---

### Post by Menyus on 2010-05-05
Additional info from log files on my last login attempt:

Xorg.0.log: no errors or warnings

auth.log:

May  5 12:19:12 UHPdv9k gdm-session-worker[1229]: pam_succeed_if(gdm:auth): requirement "user ingroup nopasswdlogin" not met by user "cnemeth"
May  5 12:19:15 UHPdv9k gdm-session-worker[1229]: pam_unix(gdm:session): session opened for user cnemeth by (uid=0)
May  5 12:19:15 UHPdv9k gdm-session-worker[1229]: pam_ck_connector(gdm:session): nox11 mode, ignoring PAM_TTY :0
May  5 12:19:15 UHPdv9k gdm-session-worker[1229]: pam_unix(gdm:session): session closed for user cnemeth
May  5 12:24:06 UHPdv9k sudo:  cnemeth : TTY=tty2 ; PWD=/home/cnemeth ; USER=root ; COMMAND=/bin/kill -TERM 974
May  5 12:24:36 UHPdv9k polkitd(authority=local): Registered Authentication Agent for session /org/freedesktop/ConsoleKit/Session7 (system bus name :1.45 [/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1], object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_US.UTF-8)
May  5 12:24:57 UHPdv9k gnome-keyring-daemon[1897]: PROMPT INPUT:#012#012[prompt]#012title=Unlock Login Keyring#012primary=Enter password to unlock your login keyring#012secondary=The login keyring did not get unlocked when you logged into your computer ...
May  5 12:25:02 UHPdv9k gnome-keyring-daemon[1897]: PROMPT OUTPUT:#012...[transport]#012public=EC120 ... 2#012[password]#012parameter=E7D0...C97AE2#012value=A175...2#012[unlock-options]#012unlock-auto=false#012unlock-timeout=0#012unlock-idle=0#012#012[details]#012expanded=false#012#012[prompt]#012response=ok#012

messages:

May  5 12:25:04 UHPdv9k kernel: [  940.738591] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
May  5 12:25:05 UHPdv9k kernel: [  940.961170] Intel AES-NI instructions are not detected.
May  5 12:25:05 UHPdv9k kernel: [  941.083147] padlock: VIA PadLock not detected.
May  5 12:25:11 UHPdv9k kernel: [  947.906364] CE: hpet increasing min_delta_ns to 15000 nsec

Nothing of interest seems to be in the syslog and user.log files

Thanks.

---

### Post by Menyus on 2010-05-05
This is my /etc/pam.d/gdm:

#%PAM-1.0
auth    requisite       pam_nologin.so
auth    required        pam_env.so readenv=1
auth    required        pam_env.so readenv=1 envfile=/etc/default/locale
auth    sufficient      pam_succeed_if.so user ingroup nopasswdlogin
@include common-auth
auth    optional        pam_gnome_keyring.so
@include common-account
session [success=ok ignore=ignore module_unknown=ignore default=bad] pam_selinux.so close
session required        pam_limits.so
@include common-session
session [success=ok ignore=ignore module_unknown=ignore default=bad] pam_selinux.so open
session optional        pam_gnome_keyring.so auto_start
@include common-password

---

### Post by Menyus on 2010-05-05
/etc/gdm directory content:

cnemeth@UHPdv9k:~$ ls -al /etc/gdm
total 68
drwxr-xr-x   6 root root  4096 2010-04-29 05:44 .
drwxr-xr-x 138 root root 12288 2010-05-05 12:25 ..
-rw-r--r--   1 root root   132 2010-04-01 04:07 failsafeBlacklist
-rwxr-xr-x   1 root root  8778 2010-04-01 04:07 failsafeXinit
-rwxr-xr-x   1 root root  4778 2010-04-01 04:07 failsafeXServer
-rw-r--r--   1 root root  3157 2010-04-14 23:57 gdm.schemas
drwxr-xr-x   2 root root  4096 2010-04-29 05:44 Init
drwxr-xr-x   2 root root  4096 2010-04-29 05:44 PostLogin
drwxr-xr-x   2 root root  4096 2010-04-29 05:44 PostSession
drwxr-xr-x   2 root root  4096 2010-04-29 05:44 PreSession
-rwxr-xr-x   1 root root  6017 2010-04-14 23:56 Xsession
cnemeth@UHPdv9k:~$

---

### Post by WorMzy on 2010-05-05
Why are you changing the PATH variable? Is it not set by default?

Do ```
cat /etc/environment
```does it return: ```
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
```
If not, make it say that with a text editor like vi or nano. You may need to type this into a console first: ```
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
```

---

### Post by Menyus on 2010-05-05
My /etc/environment has the same PATH but when I login through the console, PATH is not set and I have to set it manually.

---

### Post by Menyus on 2010-05-05
My /etc/environment has the same path but when I login through the console, I have to set it manually every time

---

### Post by WorMzy on 2010-05-05
That might one of the symptoms of an underlying problem, my PATH variable is set in ttys when I log into one. I suspect that there's something wrong with your home folder that's causing these problems, but as to what it might be, I have no idea. Maybe someone else can shed some light on the matter, as I have no more advice to offer. Sorry. :(

---

### Post by Menyus on 2010-05-05
Thanks anyway, It may be time to think about rebuilding from scratch ...

---

### Post by Menyus on 2010-05-06
I created a new user, which seem to have solved the problem.

---

### Post by Ambidextrous on 2010-05-15
I started to have the same problem - someone else called it a "Logon Loop".

I tried
 
```
sudo pkill gdm
startx 
```I get a fatal error:  X-Server is running.  So I tried 
 
```
sudo rm /tmp/.X0-lock 
```which didn't help.

I read in another thread that ~.Xauthority and ~.ICEauthority could  cause the problem, so I deleted both.  No change.  In this thread  the original poster reported that he had solved the problem by creating a  new user.  In another thread someone wrote that ~.profile had been the problem but neglected to explain what the problem was, or how s/he fixed it.  

I didn't want to re-do all the customization I'd done so I renamed ~.profiles to  ~.profile_old and tried again.

This time I got a black screen with a mouse cursor.  Not really the  solution I'd been hoping for.

I used nano to examine ~.profile_old.  I found no smoking gun, so I  renamed it back to ~.profile and tried again.

> **WorMzy said:**
> Go to a tty (Ctrl+Alt+F1) and log in, then try running 'startx'. Does it cause the same behaviour?

If so, also in a tty, run 'sudo apt-get purge nvidia-*' and then 'startx' again.

Un-installing the Nvidia drivers turned out to be a [SIZE=4]**really**[/SIZE] bad idea.  After I ran this I was unable to boot to anything, even recovery mode.

I had no alternative, I had to re-install.

Your mileage may vary. :(

---

### Post by ZarlacMing on 2010-05-18
A solution to the problem about the gnome keyring that pops up after every login can be resolved by doing this:

[http://www.noob2geek.com/how-to/how-to-disable-gnome-keyring-in-ubuntu-10-04/](http://www.noob2geek.com/how-to/how-to-disable-gnome-keyring-in-ubuntu-10-04/)

---

