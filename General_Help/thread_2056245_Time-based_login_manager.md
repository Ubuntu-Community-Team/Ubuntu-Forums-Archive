---
title: "Time-based login manager"
date: 2012-09-11
forum: General Help
---

### Post by cwwilson721 on 2012-09-11
My Ubuntu box is used by all members of my family.

I cannot count the number of times one of my kids is on at 2:30am.

Is there any type of program out there that would only allow them on between certain hours?

An example is my router has a scheduler that allows me to block devices from getting online between two time periods I've set.

I'm not talking about that, but to stop them from even logging on to their account between, say, 11pm and 7am?

---

### Post by dodo3773 on 2012-09-11
> **cwwilson721 said:**
> My Ubuntu box is used by all members of my family.

I cannot count the number of times one of my kids is on at 2:30am.

Is there any type of program out there that would only allow them on between certain hours?

An example is my router has a scheduler that allows me to block devices from getting online between two time periods I've set.

I'm not talking about that, but to stop them from even logging on to their account between, say, 11pm and 7am?

You need to write a daemon or put something early in your startup in your init system. Here is the code I use:

```

hr=$(date | awk '{print $4}' | cut -f"1" -d":")
(( hr < 7 || hr > 22 )) && poweroff

```

I guess you can just put that in a script and add it to roots crontab (and save it somewhere that cannot be removed without root permissions like /usr/bin, etc..etc...). The computer will boot and then just shut itself back down.


If the above code gives you problems for any reason here is my original script (it should be pretty self explanatory):
```

timeofday=$( date | awk '{print $4}' | cut -f"1" -d":" )

if [ "$timeofday" -gt "7" ] && [ "$timeofday" -lt "22" ] ; then
echo "boot"
else
poweroff
fi

```

---

### Post by Lars Noodén on 2012-09-11
timeofday can be made even shorter by taking advantage of the formatting capabilities in [date](http://manpages.ubuntu.com/manpages/precise/en/man1/date.1posix.html)

```

timeofday=$(date +"%H")

```

See the manual page for the full list of date formatting options.

---

### Post by dodo3773 on 2012-09-11
> **Lars Noodén said:**
> timeofday can be made even shorter by taking advantage of the formatting capabilities in [date](http://manpages.ubuntu.com/manpages/precise/en/man1/date.1posix.html)

```

timeofday=$(date +"%H")

```

See the manual page for the full list of date formatting options.

You're right. It is much cleaner code that way. Someone pointed this out to me before but I didn't change my script. Thanks

---

### Post by cwwilson721 on 2012-09-11
Getting there, but not quite what I want.

The comp is on 24/7 as server(s). I just need to restrict certain users to certain hours, not shut the whole thing off at certain times (I can already do that, if I wish)

Some users need access at various hours, while some shouldn't

---

### Post by Lars Noodén on 2012-09-11
It's been ages and ages since I've even looked at [PAM](http://www.linuxjournal.com/article/2120) but it might do what you want.  There is a file [/etc/security/time.conf](http://manpages.ubuntu.com/manpages/precise/en/man5/time.conf.5.html) which can restrict logins based on time.

Here's one article covering it:

[http://www.techrepublic.com/article/using-pam-to-restrict-access-based-on-time/1055269](http://www.techrepublic.com/article/using-pam-to-restrict-access-based-on-time/1055269)

If you figure it out, please post what you needed to do to get it to work.  It'd be interesting to see.

Edit: I've got it working for ssh.  The line [font=Courier New]account required pam_time.so[/font] also needs to be added to the end of the appropriate file in the directory /etc/pam.d/  For ssh, it is the file sshd.  For lightdm, the display manager, it will be something else.

Edit: It looks like the right file for the graphical login is /etc/pam.d/lightdm

---

### Post by HermanAB on 2012-09-11
Another way is to set up an Internet Cafe system:
[http://www.zencafe.web.id/release-zencafe-22/](http://www.zencafe.web.id/release-zencafe-22/)
[http://www.vibersoft.com/cyber_cafe_software.htm](http://www.vibersoft.com/cyber_cafe_software.htm)

The advantage is much more control.

---

### Post by cwwilson721 on 2012-09-11
> **HermanAB said:**
> Another way is to set up an Internet Cafe system:
[http://www.zencafe.web.id/release-zencafe-22/](http://www.zencafe.web.id/release-zencafe-22/)
[http://www.vibersoft.com/cyber_cafe_software.htm](http://www.vibersoft.com/cyber_cafe_software.htm)

The advantage is much more control.

That is SO out of whack to my question...

I'm **NOT**:
[LIST]
[*]Installing another OS when this one does everything I want. If I wanted to change, it would be back to Slackware.
[*]Limiting Internet
[*]Access from other computers to the LAN(Can do that thru router firmware anyway)
[/LIST]

I AM trying to STOP _*LOGINS*_ on ONE computer to certain users at certain times. GNOME NANNY doesn't work, TIMEKPR won't work on 12.04.

I'll try Lars Noodén idea when my brain can handle the concept (almost 6am here, been up all night)

---

### Post by newb85 on 2012-09-11
> **cwwilson721 said:**
> That is SO out of whack to my question...

I'm **NOT**:
[LIST]
[*]Installing another OS when this one does everything I want. If I wanted to change, it would be back to Slackware.
[*]Limiting Internet
[*]Access from other computers to the LAN(Can do that thru router firmware anyway)
[/LIST]

I AM trying to STOP _*LOGINS*_ on ONE computer to certain users at certain times. GNOME NANNY doesn't work, TIMEKPR won't work on 12.04.

I'll try Lars Noodén idea when my brain can handle the concept (almost 6am here, been up all night)

My experience with Gnome-nanny:

--User login prevention has been broken since Ubuntu switched to LightDM.
--It has a missing dependency that will be taken care of if you install Gnome metapackage.
--Scheduling for Browser, email, etc. is all done in GMT.

So, if you install Gnome, then reinstall Gnome-nanny, it won't prevent your kids from being on the machine at all hours, but it can restrict their internet use.  (If their activities require internet, this will probably kill their interest...)

---

### Post by dodo3773 on 2012-09-11
There should be options to run a script at boot from lightdm. Something like this in /etc/lightdm/lightdm.conf 
```

greeter-setup-script=/path/to/script

```

Of course you can probably use something else that is sourced when someone logs in. There is probably more than one way to do it. In your script just put an if $USER and if $time then logout type script. Should be pretty straight forward.

---

### Post by Lars Noodén on 2012-09-12
Looking at PAM a little more, it looks like you can do it easily.  

At the end of /etc/pam.d/login and /etc/pam.d/lightdm add to the end or uncomment this line:

```

account    requisite  pam_time.so

```

In time.conf add something like this:

```

lightdm;tty*;@kids;Wk0700-2200
login;tty*;@kids;Wk0700-2200

```

'kids' is a group and the kids accounts need to be members.  Using a group will eliminate the need to write in all the names.

Which version of Ubuntu are you using?  It is using LightDM right?

---

