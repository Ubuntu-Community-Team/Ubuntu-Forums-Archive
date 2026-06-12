---
title: "How to remove users from login window?"
date: 2009-10-30
forum: General Help
---

### Post by abcuser on 2009-10-30
Hi,
on Ubuntu 9.10 there is login window. I have multiple users defined on system, but I don't want all of them to be displayed on login window. How to remove users from login window?
Regards

---

### Post by P4man on 2009-10-30
At this point, I dont think you can. Tools to customize the new gdm login screen are still being worked on, what we have now is rudimentary at best (as you.ve probably noticed)

---

### Post by elleP on 2009-10-30
That's horrible :)
I am the only graphical user for my system, but there are about 15 users that use it for remote access.

---

### Post by larytet on 2009-10-31
I am missing this feature too.  I have lot of users, like qemu, vsftp and others who will never login. In the previous login (9.04) when typed user name it was easier, than scrolling through the list.

I suspect also, that exposing user names reduces security.

---

### Post by arepaking on 2009-10-31
I also need to hide the user names. It is unbelievable that this new Ubuntu version forces you to display the user accounts. Hopefully we will have a solution for this with an update.

---

### Post by crazycatlady0 on 2009-10-31
this is a bummer... and a potential security risk.

are there any other login screen options for 9.10?  Can i use kdm instead?   Can I use some other terminal login instead?

---

### Post by P4man on 2009-10-31
There seems to be solution for the not showing all users. Have a look here:
[http://www.ubuntuforums.org/showthread.php?t=1300640](http://www.ubuntuforums.org/showthread.php?t=1300640) (post n5 and beyond)

Funny, it was a response to arepaking, who also posted here, but apparently missed the reply with the solution in his own thread? Either that or its not working, I havent tried it yet.

---

### Post by abcuser on 2009-11-01
> **P4man said:**
> There seems to be solution for the not showing all users. Have a look here:
[http://www.ubuntuforums.org/showthread.php?t=1300640](http://www.ubuntuforums.org/showthread.php?t=1300640)
Solution in above thread is to remove all users from the list and enable username login window instead.

But I don't want to remove user list. I would just like to remove some users from the list.

---

### Post by DaleyKD on 2009-11-02
I too would like to find out how to remove users from this log in screen.

I'll go ahead and set a watch to this thread.  :)

---

### Post by arepaking on 2009-11-02
There is a gconf setting for it:

```
sudo -u gdm gconftool-2 --type bool --set /apps/gdm/simple-greeter/disable_user_list 'true'
```

---

### Post by abcuser on 2009-11-03
arepaking, this is the same solution that was described on above link, I don't like this solution. It removes whole list and enables login with userid window to enter manually.

I would like ot have a user list (like it is now), but without some users listed on it.

---

### Post by tristano on 2009-11-04
As a workaround, user IDs can be changed to remove users from the login list. Users with IDs under 1000 will not be displayed. I used the following to remove a user from the list:
```
sudo usermod -u 999 [username]
```
Not ideal, but it works without much hassle.

---

### Post by windowsdown on 2009-11-23
> **abcuser said:**
> Solution in above thread is to remove all users from the list and enable username login window instead.

But I don't want to remove user list. I would just like to remove some users from the list.

This is what I would up doing.  I made the gconf-edit changes, but they did not changethe interface, so...

* Consider going in as root...then...
1. System/Administration/Users and Groups
2. On the Advanced tab of user Properties...
3. Change the User ID to a number that is less than 1000.

Far as I can tell, this also takes the user account out of the Users and Groups screen, thus removing your ability to administer the account outside the terminal, but who doesn't use the terminal to admin users anyway?

---

### Post by abcuser on 2009-11-25
windowsdown,
I did in the way tristano suggested, so lower ids of users and problem is solved.

Before I have changed the IDs I have checked the IDs of exiting users, to not having any kind of conflict.

Check the users IDs:
```
cat /etc/passwd | gawk -F: '{print $3, $1}' | sort -n
```

Lower users IDs (tristano suggestion):
```
sudo usermod -u 999 [username]
```

Thanks a lot for help,
Regards

---

### Post by buck2825 on 2009-11-30
I have a Dell D620 running 32-bit 9.10 

every time / every way I try to change the key "disable_user_list"

I get an error or the GUI shows "this key not writable"

any ideas

thanks

---

### Post by abcuser on 2009-12-01
> **buck2825 said:**
> every time / every way I try to change the key "disable_user_list"
Hi,
what are you trying to do? Where is settings "disable_user_list"? Can you please write more detailed info.
Regards

---

### Post by buck2825 on 2009-12-01
> **abcuser said:**
> Hi,
what are you trying to do? Where is settings "disable_user_list"? Can you please write more detailed info.
Regards


I am trying to remove the list of users from the gdm welcome screen

in the configuration editor
/apps/gdm/simple-greeter/disable_user_list

or by typing 
sudo -u gdm gconftool-2 --type bool --set /apps/gdm/simple-greeter/disable_user_list 'true'

I have tried making this change by launching the configuration editor from the application menu, from TTY1 before login by launching the editor, and using the above terminal command.

thanks for the help

---

### Post by HiImTye on 2009-12-01
> **windowsdown said:**
> This is what I would up doing.  I made the gconf-edit changes, but they did not changethe interface, so...

* Consider going in as root...then...
1. System/Administration/Users and Groups
2. On the Advanced tab of user Properties...
3. Change the User ID to a number that is less than 1000.

Far as I can tell, this also takes the user account out of the Users and Groups screen, thus removing your ability to administer the account outside the terminal, but who doesn't use the terminal to admin users anyway?
/apps/gnome-system-tools/users/showall
toggle that and you can see all users

---

### Post by rpaskudniak on 2009-12-01
I have two remarks about this thread AKA my $0.02 (USD)

First:
> Tristano supplied this exceedingly cool tidbit of hacker knowledge:
As a workaround, user IDs can be changed to remove users from the login list. Users with IDs under 1000 will not be displayed. I used the following to remove a user from the list:

```
sudo usermod -u 999 [username]
```
That looks like a winning solution than everything else I have seen in this thread.  I was wondering if I could add postgres to the login menu (also if I should - I decided against).  Just one fly in the ointment:  You would have to track down every blessed file in the system whose UID matches the current UID and change it to the new one.

I see abcuser has already accounted for the concern of duplicating a UID.  I just wanted to raise this little warning.

Next, HiImTye suggested to windowsdown:
> [FONT="Courier New"]/apps/gnome-system-tools/users/showall[/FONT]
toggle that and you can see all users
Which tool is that?  I have 9.10 and I do not even have an /apps directory, let alone the three directory levels below it.  A quick check of Synaptic shows I do indeed have a package named gnome-system-tools installed but is seems to be a directory in /etc; it's only claim to fame (AFAIK) is the file
  [FONT="Courier New"]/etc/gnome-system-tools/users/profiles[/FONT].

Care to rephrase that command line, Tye?  (Gee, that sounded threatening.. :lolflag:  )

---

### Post by buck2825 on 2009-12-02
so still no solution NOT SOLVED I want a login screen just like in 9.04  

boot 
enter user name
enter password
ta da!!!

I don't want to have a list for everyone to see of all users on my machine.  also an advantage of ubuntu no root user enabled, I don't want to enable it because well then everyone now knows my user name.

so I have tried everything I have seen on every forums.  any new suggestions will help.

Thanks in advance

---

### Post by joes7 on 2009-12-08
Simply delete the user by going to Applications->System->Users and Groups and delete the selected user.

---

### Post by rpremuz on 2009-12-14
> **abcuser said:**
> arepaking, this is the same solution that was described on above link, I don't like this solution. It removes whole list and enables login with userid window to enter manually.

I would like ot have a user list (like it is now), but without some users listed on it.

The **GNOME Display Manager Reference Manual**, which you can get through the Ubuntu Help Center (? icon on the Top Edge Panel), says in chapter 5.5.,&#8195;"Simple Greeter Configuration", that some users can be excluded from the Face Browser (that's the name of the users list) using the following command:

```
sudo -u gdm gconftool-2 --type list --list-type=string --set /apps/gdm/simple-greeter/exclude '[john;mary]'

```

BUT, according to [https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/480658](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/480658) the documentation is incorrect as this feature hasn't been implemented yet!

-- rpr.

---

### Post by specialcowboy on 2010-02-03
> **arepaking said:**
> There is a gconf setting for it:

```
sudo -u gdm gconftool-2 --type bool --set /apps/gdm/simple-greeter/disable_user_list 'true'
```


I too wanted to remove usernames from the logon window in Karmic.  Certainly don't want them displayed in general.  I preferred the way it was in Jaunty.  Thanks for the gconf setting. Worked great.

---

### Post by OzzyFrank on 2010-06-10
Interesting thread. Someone just asked me about achieving this, so am wondering does the following command (which hadn't actually been implemented in Gnome yet, but apparently now is) works, at least with 10.04 (which apparently it should now):
[B]
sudo -u gdm gconftool-2 --type list --list-type=string --set /apps/gdm/simple-greeter/exclude '[insertusername]'
[/B]
Thanks

---

### Post by Tobu on 2010-06-16
@OzzyFrank, that works, with a slightly different syntax.

You have to put this in /etc/gdm/custom.conf (or the old /etc/gdm/gdm.conf if it exists):

```
[greeter]
# Default value taken from /etc/gdm/gdm.schemas
Exclude=USER_TO_EXCLUDE,bin,root,daemon,adm,lp,sync,shutdown,halt,mail,news,uucp,operator,nobody,nobody4,noaccess,postgres,pvm,rpm,nfsnobody,pcap
```

Note that this doesn't prevent users from logging in if they still have shell access.

---

### Post by UselessTool on 2010-08-01
I,ve tried Tobu's method and it works well when excluding one user.

I was wondering, how do I do this for multiple users?
Not only just one.

The futile attempts I have made do not seem to cut it :)

Br,

---

### Post by Thunderbolt1164 on 2010-09-02
tristano:

sudo usermod -u 999 [username]

Thank-you for this tip
It still works in Ubuntu 10.04 LTS
I was able to remove my Administrator account from the login screen, all others are Desktop Users ONLY.
By clicking Other (@ the bottom) then entering info, I am still able to log in as Administrator
Thank-you again

---

### Post by rha7dotcom on 2010-12-01
In Ubuntu 10.10 you remove users from the list by adding them to the default element in the greeter/Exclude schema in the file /etc/gdm/gdm.schemas:

```

     75     <schema>
     76       <key>greeter/Exclude</key>
     77       <signature>s</signature>
     78       <default>asterisk,bin,root,daemon,adm,lp,sync,shutdown,halt,mail,news,uucp,operator,nobody,nobody4,noaccess,postgres,pvm,rpm,nfsnobody,pcap</default>
     79     </schema>

```

Works for me to remove the asterisk user from Face List, hope it works for you too.

Gabriel Medina (Rha7).

---

### Post by sceo on 2011-02-09
For 10.10, is there a config file I could put in my home or something so that it won't get overwritten (or I won't even have to be prompted) if I upgrade gdm?

---

### Post by tristano on 2011-02-13
Thunder, you should be able to use the method described by rha7 to exclude users in 10.04 rather than that UID hack. The tip was for 10.10, but I can confirm that /etc/gdm/gdm.schemas and the corresponding greeter/Exclude key exist in 10.04 as well.

sceo, since GDM is a system wide service, you cannot configure it within your home directory. There isn't any sort of conf.d directory for GDM, either, so I don't think you can do what you want to do.

---

### Post by sceo on 2011-02-13
Actually I found it while perusing a Fedora forum.  The file is /etc/gdm/custom.conf and it's got an ini-file like syntax.


[greeter]
Exclude=youruser,nobody

Notice - when I only put "youruser" then "nobody" showed up on the login screen, so I just added nobody second.

---

### Post by tristano on 2011-02-13
Of course you can do what you want to do, this is Linux! Very cool that you figured it out and thanks for sharing. It seems the reason you need to include nobody is because your custom.conf overrides the list in gdm.schemas. Your greeter/Exclude in there probably includes these users:

```

bin,root,daemon,adm,lp,sync,shutdown,halt,mail,news,uucp,operator
,nobody,nobody4,noaccess,postgres,pvm,rpm,nfsnobody,pcap

```

Some of those might not even be real users on the system and most do not have a UID of 1000 or greater (thus they will not appear in the greeter anyway). This is not the case for nobody, which has a UID of 65534. So that explains why you need to "re-add" it to the custom exclude list.

It would be nice if the entry in custom.conf could append to the Exclude list rather than overwrite it... but it sure beats hacking user IDs!

---

### Post by spufidoo on 2011-02-15
That's just what I wanted after installing DB2.
Thanks.

---

