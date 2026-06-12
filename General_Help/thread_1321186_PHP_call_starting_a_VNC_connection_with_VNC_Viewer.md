---
title: "PHP call starting a VNC connection with VNC Viewer Listening mode"
date: 2009-11-09
forum: General Help
---

### Post by Camicia on 2009-11-09
I have problem with the firewall at work that doesn't let me to open a port on our server. The only open port is the 80 (for the web server).

I am trying to create a script that once I hit the server on a specific page, it runs "x11vnc -display :0 -connect xxx.xxx.xxx.xxx -noxdamage" using the PHP function 'exec'. 

If I run the command from command line in a shell the VNC works find but if I am trying to do that through 'exec' in a PHP script, it doesn't work. 

I think the problem is that the user running apache2 is www-data. 
But I am not sure how to solve the problem.

Can you help me with that?

Best,
   Camicia

---

### Post by krunge on 2009-11-09
> 
I think the problem is that the user running apache2 is www-data. 
But I am not sure how to solve the problem.

The www-data user (likely) does not have permission to connect to your X display :0.

You need to open that up somehow, either by sharing the contents of your ~/.Xauthority mit-cookie file (see the x11vnc -auth option), or more drastic running 'xhost +'.  See the xhost(1) manpage for more info and safer possibilities.

---

### Post by Camicia on 2009-11-10
Thank you for the answer.
I am pretty a newbie with X.

My approach was more trying to make the script as it was run by a different user. 

Do you mind to write an example of what you think may work?
Do you think I could get running a VNC connection to a brand new X interface on another display? How?

Best,
   Chris

---

### Post by krunge on 2009-11-10
> **Camicia said:**
> 
My approach was more trying to make the script as it was run by a different user.

The X permissions prohibit (in a soft sort of way) other users from connecting to your X session (desktop) unless you explicitly allow them to.

Even root (i.e. sudo) will have trouble connecting (unless he can read your ~/.Xauthority cookie file, where the secret keys are kept.)

More info here:
[INDENT][http://www.karlrunge.com/x11vnc/faq.html#faq-xperms](http://www.karlrunge.com/x11vnc/faq.html#faq-xperms)[/INDENT]

>  
Do you mind to write an example of what you think may work?

Well, here is a simple one. I assume your home directory is /home/chris. **After** you log into your desktop, execute these commands:
```

cp /home/chris/.Xauthority /tmp/.Xauthority.copy
chmod 644 /tmp/.Xauthority.copy

```
(maybe you can have a desktop startup script automate this for you.)

Then change your php script to put the -auth option on the x11vnc cmd line:
```

x11vnc -auth /tmp/.Xauthority.copy -display :0 ....

```
(note that this might not work on ubuntu 9.10 because GDM removed this functionality that has been around for 20 years.)

An even simpler alternative is to just run this after you login and from **inside** your desktop (e.g. inside a terminal):
```

xhost +

OR:

xhost +local:

```
but that is rather drastic since it removes all access control so think about what you are doing first (BTW, my example above is similarly flawed and relies on no one finding the copy.)

If you read the xhost man page:
```
man xhost
```
you will find more information.

Another option is to have the php script run as your own user id.  I know that is possible to set up in apache for cgi scripts, but I haven't done it in a while.

---

### Post by Camicia on 2009-11-23
Thanks. I was able to create the script. I added this to my .bashrc:
```
xdbfile=`xauth info | awk '/Authority file:/ {print $3}'`
cp $xdbfile /tmp/xcookie
chmod 644 /tmp/xcookie
```
and this is in my script:
```
nohup x11vnc -display :0 -auth /tmp/my_xcookie -connect xxxx &
```

Now it is working.
The only problem is how can I access the vnc when ubuntu restart?
Right now in order to connect I need at least to login into the computer and launch a Xterm window (that I think is launching the .bashrc).

Thank you again for the help.

---

### Post by krunge on 2009-11-23
> 
and this is in my script:
```
nohup x11vnc -display :0 -auth /tmp/my_xcookie -connect xxxx &
```

Just so that I have it clear; that script is run by PHP thru apache as user www-data?
> 
The only problem is how can I access the vnc when ubuntu restart? Right now in order to connect I need at least to login into the computer and launch a Xterm window (that I think is launching the .bashrc).

You might be able to do this (i.e. before user logs into a desktop X session) via your display manager setup script.  E.g. for GNOME's GDM:
```
/etc/gdm/Init/Default
```
(but it might be named something else depending on your distro and display manager)

More info here:
[INDENT][http://www.karlrunge.com/x11vnc/faq.html#faq-display-manager](http://www.karlrunge.com/x11vnc/faq.html#faq-display-manager)[/INDENT]
Ask if it is not clear what to do in that script.

---

### Post by Camicia on 2009-11-24
I am using Ubuntu 9.10. Let me explain briefly the bigger picture. 
The sysadmin is being difficult and he thinks that even the SSH port is unsecure (well there is a reason, in the lab there was a computer that was violated before through SSH, probably with a dictionary attack). So the only ports that he left us opened are port 80 and 81.
I need to do some development from home on the machine. I use PHP/MySQL. I want to be able to run the critical updates and being able to upload php/images files to the server. Eventually to do some remote debugging (maybe with xdebug). 
I thought that if I can have access to the graphical shell, I can keep working from home to make things smoothly. I want eventually to be able to upload/download files quickly.
Any suggestion is welcomed on this.

**Now current problem:**
The script "x11vnc ... - connect ..." is called by PHP. So when apache is running I am able to hit it. The user is www-data. The problem is if I need to restart the the server, at login my user has not log into the shell yet, so the code in .bashrc was not executed.

The other 3 lines of script in .bashrc copy the cookie that may change position at each login. I found it using "xauth info" that told me something like "Authority file: /var/run/gdm/auth-for-chris-qqwewq/database". The qqwewq is variable. The first line in the script find the path and the other 2 lines are what Krunge was suggesting.

I want that after I restart the computer for some reasons I am able to access the machine. Maybe the easiest way would be an automatic login from my user but I don't know how.

Krunge was suggesting to dig into /etc/gdm/Init/Default. I looked into that but I am not sure what to do. Should I add the 3 lines that are now in .bashrc? 

I am also not sure if the X graphical interface user at that time is my user (chris). I think it is something else, not sure.

I need more help on this.

Best, 
    Camicia.

P.s.: I noticed that the VNC connection is pretty slow.

---

### Post by krunge on 2009-11-25
> 
Krunge was suggesting to dig into /etc/gdm/Init/Default. I looked into that but I am not sure what to do. Should I add the 3 lines that are now in 
.bashrc? 

Basically, yes.  That script is run as root every time the X server starts up. No one is logged in yet, just the gdm login greeter is running. So in principle that script can copy the xauthority cookie for you to the right place.

On ubuntu 9.04 and earlier it was trivial (see the link I gave) On 9.10 the new gdm makes it difficult.  I suspect you rummage around in /var/run/gdm for it, then copy it.

Are you able to edit /etc/gdm/Init/Default on this machine, or can only the sysadmin do that?
> 
I am also not sure if the X graphical interface user at that time is my user (chris). I think it is something else, not sure.

Yes that's fine.  It should be the gdm login greeter.  Read the link I provided.
> 
P.s.: I noticed that the VNC connection is pretty slow.
That's too bad.  Maybe you can quantify.

---

### Post by Camicia on 2009-11-25
Yes, I can sudo into the machine. I will try this Friday when I will be on the machine. I don't want to reboot now from home and be lock out.

Regarding speed: The mouse is pretty responsive. However **I often type stuff on gedit and I have to wait 5+ secs before to see the updates**. Moving windows around is it actually faster.  
X DAMAGE is on. I saw XDAMAGE errors before when I was testing from the lab . 
The server has a n NVIDEA 84000 GS (I Think) that has some hw acceleration. 
fb read rate: 827 MB/sec

---

### Post by krunge on 2009-11-25
> Yes, I can sudo into the machine. I will try this Friday when I will be on the machine. I don't want to reboot now from home and be lock out.

OK.  Just do the steps manually the first time as root (sudo -i) with nobody logged into the desktop. Test that it works for your PHP app as you want. Then automate those steps you figured out and put them into /etc/gdm/Init/Default near the bottom.
> 
Regarding speed: The mouse is pretty responsive. However **I often type stuff on gedit and I have to wait 5+ secs before to see the updates**. Moving windows around is it actually faster.  X DAMAGE is on. I saw XDAMAGE errors before when I was testing from the lab.  The server has a n NVIDEA 84000 GS (I Think) that has some hw acceleration. 

Are you using the x11vnc "-noxdamage" option or not?  In your first post you mention using it.  From your description it sounds like you are now not using "-noxdamage", but should be (to avoid slow updates.) Or you can disable compiz, etc. Xorg + nvidia drivers are broken WRT XDAMAGE for many years.

---

### Post by Camicia on 2009-11-26
> **krunge said:**
> OK.  Just do the steps manually the first time as root (sudo -i) with nobody logged into the desktop. Test that it works for your PHP app as you want. Then automate those steps you figured out and put them into /etc/gdm/Init/Default near the bottom.


When should I run "sudo -i" ? If I don't login in, how can I enter any command?
I was reading at your answer on this post: [http://ubuntuforums.org/showthread.php?t=1336462](http://ubuntuforums.org/showthread.php?t=1336462)
I think that the 443 solution will work great for me too. I didn't think about that but it would be actually more flexible than my solution.
I have questions about that:
1 - Currently apache is not listening on 443 port. But I have to use sudo in order to launch the X11vnc on 443. Why?  ```
sudo x11vnc -display :0 -rfbport 443 -usepw 
```2 - I tried : ```
 sudo x11vnc -display :0 -rfbport 443 -usepw -ssl SAVE -https 
``` Contrary to the other guy I cannot see any message about the Java Client. Infact connecting on https: I get  only : "RFB 003.008". {edited} I installed the tight-java and added the parameter" -httpdir /usr/share/tightvnc-java/" but connecting to [https://my.no-ip.com/?PORT=443](https://my.no-ip.com/?PORT=443) I can see the java client but after entering the password I get the error: "network error: remote side closed connection"
3 - Can I just add the previous code into /etc/gdm/Init/Default and it will enable me to be able to VNC in on the login screen and after I am logged-in? 
4 - How secure is the [connect_switch]("http://www.karlrunge.com/x11vnc/connect_switch") ? I am afraid about someone that can exploit it and run malicious commands on the machine.
5 - I am pretty novice with SSH. I have used to connect with putty but it is pretty much it. Can I have a SSH VNC connection without having the SSH port open on the server? What do I need and how do I configure the client side (windows based)?
6 - I would be very handy if  I can access the server from anywhere without the need or installing a client. How can I simple use the browser to connect and run the JavaClient throught the same port?

> **krunge said:**
> 
Are you using the x11vnc "-noxdamage" option or not?  In your first post you mention using it.  From your description it sounds like you are now not using "-noxdamage", but should be (to avoid slow updates.) Or you can disable compiz, etc. Xorg + nvidia drivers are broken WRT XDAMAGE for many years.

I used -noxdamage and then I removed it. After you wrote me last message I tried to enable and it working better.  I finally used: 
```
metacity --replace &
killall compiz compiz.real
```And now it seems to work pretty smoothly. Was this what you meant when you wrote me to disable compiz?

Thanks a lot!

---

### Post by krunge on 2009-11-26
> 
I used -noxdamage and then I removed it. After you wrote me last message I tried to enable and it working better.  I finally used: 
```
metacity --replace &
killall compiz compiz.real
```And now it seems to work pretty smoothly. Was this what you meant when you wrote me to disable compiz?

Yes, That's the spirit!  I love people who disable compiz (and the way you use killall is particularly inspiring.)

Using x11vnc -noxdamage does provide a workaround, but by disabling compiz you let x11vnc use XDAMAGE and there can be a nice improvement in interactive response (especially for typing response or other small changes on the screen); and a decrease in system load too.

I will answer your other questions tomorrow.

---

### Post by krunge on 2009-11-26
> 1 - Currently apache is not listening on 443 port. But I have to use sudo in order to launch the X11vnc on 443. Why?

Only root can listen on ports less than 1024.

---

### Post by krunge on 2009-11-26
> 
3 - Can I just add the previous code into /etc/gdm/Init/Default and it will enable me to be able to VNC in on the login screen and after I am logged-in? 

Yes to both.  You will need to see if your 'xauth info' trick works in that environment. Otherwise you will need to do something else.

Maybe the value of the env. var. $XAUTHORITY will contain the filename; which is even simpler (just cp $XAUTHORITY /the/place, etc.)

BTW, For GDM you will need to set KillInitClients=false in its gdm.conf file so it won't kill all initial X clients (x11vnc in this case.) Unfortunately this no longer work with GDM in ubuntu 9.10 (the upstream x11vnc 0.9.9 has a workaround.)

---

### Post by krunge on 2009-11-26
> 
5 - I am pretty novice with SSH. I have used to connect with putty but it is pretty much it. Can I have a SSH VNC connection without having the SSH port open on the server? What do I need and how do I configure the client side (windows based)?

To redirect SSH connections with the 'connect_switch' tool you will need an ssh client that can use a Web Proxy.  Then set the proxy to be your-ip:443 (or whatever port you decide to use.) I think Putty supports web proxies.

It is all described here including example for unix ssh via the ProxyCommand option:
[INDENT][http://www.karlrunge.com/x11vnc/ssl-single-443.html](http://www.karlrunge.com/x11vnc/ssl-single-443.html)[/INDENT]

---

### Post by krunge on 2009-11-26
> 2 - I tried : ```
 sudo x11vnc -display :0 -rfbport 443 -usepw -ssl SAVE -https 
``` Contrary to the other guy I cannot see any message about the Java Client. Infact connecting on https: I get  only : "RFB 003.008". {edited} I installed the tight-java and added the parameter" -httpdir /usr/share/tightvnc-java/" but connecting to [https://my.no-ip.com/?PORT=443](https://my.no-ip.com/?PORT=443) I can see the java client but after entering the password I get the error: "network error: remote side closed connection"

The java viewer in 'tight-java' or any other similar package doesn't know anything about SSL.

You need the x11vnc java viewer that is SSL aware. You can get it in an x11vnc source tarball (just point your -httpdir to the right place.)  Also the x11vnc 0.9.8 .deb package in squeeze/sid has it and has been reported to work.

---

### Post by krunge on 2009-11-26
> 4 - How secure is the [connect_switch]("http://www.karlrunge.com/x11vnc/connect_switch") ? I am afraid about someone that can exploit it and run malicious commands on the machine.

I think it's pretty secure.  It doesn't run external commands, all it does it redirect connections to apache or hostname:tcpport pairs that you specify in a fixed list.  If the CONNECT request is not on the list the connection is dropped.

---

### Post by krunge on 2009-11-26
> 
6 - I would be very handy if  I can access the server from anywhere without the need or installing a client. How can I simple use the browser to connect and run the JavaClient throught the same port?
x11vnc in SSL mode can do single port VNC/HTTPS (BTW, x11vnc 0.9.6 and later can do non-SSL single port as well.)

You will need the x11vnc SSL aware java viewer I mentioned in an earlier post. In fact, the command you posted above:
```
sudo x11vnc -display :0 -rfbport 443 -usepw -ssl SAVE -https
```
will do exactly what you want once you point it to the x11vnc java applet (tip: instead of -https, use -httpdir going directly to /.../classes/ssl)

Now, if you want to fold the above functionality into the connect_switch multiplexing mechanism you will need to do a couple more things.  If you go that path and if you cannot see from the documentation what to do, just ask.

---

### Post by Camicia on 2009-11-27
> **krunge said:**
> Yes to both.  You will need to see if your 'xauth info' trick works in that environment. Otherwise you will need to do something else.

Maybe the value of the env. var. $XAUTHORITY will contain the filename; which is even simpler (just cp $XAUTHORITY /the/place, etc.)

BTW, For GDM you will need to set KillInitClients=false in its gdm.conf file so it won't kill all initial X clients (x11vnc in this case.) Unfortunately this no longer work with GDM in ubuntu 9.10 (the upstream x11vnc 0.9.9 has a workaround.)

What is the workaround? And how do I make it work? 
I have 0.9.4. How do I upgrade to 0.9.9 safely(being sure that I am not looked out)?

---

### Post by krunge on 2009-11-28
> **Camicia said:**
> What is the workaround? And how do I make it work? 
I have 0.9.4. How do I upgrade to 0.9.9 safely(being sure that I am not looked out)?
So you are on ubuntu 9.10?

Where did you get x11vnc 0.9.4?  I thought it was 0.9.3.

If you compile from the source tarball
[INDENT][http://x11vnc.sourceforge.net/dev/x11vnc-0.9.9.tar.gz](http://x11vnc.sourceforge.net/dev/x11vnc-0.9.9.tar.gz)[/INDENT]
you can copy the resulting binary to any place you want, e.g. /home/camicia/x11vnc.test   Then put "/home/camicia/x11vnc.test" everywhere you have "x11vnc".

A lot of people can't compile from source these days (the distros make it difficult to do this), so you could try one of these prebuilt binaries if you wanted to:

[INDENT][http://x11vnc.sourceforge.net/dev/x11vnc-0.9.9_TEST_i686-Linux](http://x11vnc.sourceforge.net/dev/x11vnc-0.9.9_TEST_i686-Linux)
[http://x11vnc.sourceforge.net/dev/x11vnc-0.9.9_TEST_amd64-Linux](http://x11vnc.sourceforge.net/dev/x11vnc-0.9.9_TEST_amd64-Linux)[/INDENT]

Just do 'Save As' and save it as "/home/camicia/x11vnc.test", run "chmod 755" on it, and do as I describe above.

**NOTE** in either case you must get the source tarball so you can point  -httpdir to the .../classes/ssl subdirectory of it for your java applet experiments.

---

