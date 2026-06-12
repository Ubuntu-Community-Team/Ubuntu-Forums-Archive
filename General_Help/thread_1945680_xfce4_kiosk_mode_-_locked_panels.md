---
title: "xfce4 kiosk mode - locked panels"
date: 2012-03-23
forum: General Help
---

### Post by xris_xcess on 2012-03-23
Hi:

Im setting up a computer lab in a school. I have got a main server/firewall/nfs shares setup for a group of "fat clients". These load the root system from the server (dhcp-pxe-tftp-nfs). I also have LDAP set up for client authentication.

I have chosen an ubuntu-xfce4 desktop setup for the client machines. I did a minimal ubuntu oneiric install (cli) and then added xfce4 over that. Overall I have found it to be a good balance in between usability and lighweight. I was also atracted by the kiosk mode setting which simplifies greatly the managing of a number of users and keeping things tidy and controled.

Unfortunately, I'm having great dificulty setting the kiosk mode - panel lock for xfce4.

The documentation for xfce4 explains two ways of doing this. They are similar but not quite the same. You can either create a kioskrc file in /etc/xdg/xfce4/kiosk/ , or set a "locked" atribute in the xfce4-panel.xml file in /etc/xdg/xfce4/xfconf/xml-per-channel/xfce4-panel.xml.

In either case, when I log into one of the user accounts I get "part" of the panel setup I configured, but the icons are generic and don't seem to have any effect (nothing happens when you click them). It would seem that they are empty launchers that are not configured. But if I check the main config file, they are configured there.

I'm thinking that it is a permission problem, but I have not been able to track it down.

Has anyone had any experience with this? any suggestions about how to track down the problems? Maybe a different solution?

---

### Post by lykwydchykyn on 2012-03-23
I have some thoughts on my experiences with Linux-based kiosks here:

[http://www.alandmoore.com/blog/2011/11/05/creating-a-kiosk-with-linux-and-x11-2011-edition/](http://www.alandmoore.com/blog/2011/11/05/creating-a-kiosk-with-linux-and-x11-2011-edition/)

Basically, my approach, instead of trying to "lock down" the desktop from change, was to create a master copy of the home directory I wanted, and rsync it periodically (in my case, whenever the browser was closed).

It depends on what you are setting up kiosks for, and what you want to allow the users to do, but to me it makes no sense to go out of your way to prevent users from changing things when you can just as easily blow away their changes when they're done with the kiosk.

What are these kiosks going to be used for?

---

### Post by xris_xcess on 2012-03-23
Great tip!

I see what you mean by building up a tailored system, instead of adapting a current one.

I'm still a bit miffed at the fact that xfce's kiosk mode is documented and people have got it to work successfully... just not me!!!

The machines in question are to be used in a computer lab in a school. The idea is that each student has an account which they can access from any machine. Mainly from the storage point of view, so as to have access to whatever material they have in their home folder.

The difference with respect to just a web-kiosk, is that I will be offering a regular desktop experience and several other applications (openoffice, pdf viewer, video player, paint program and several other education stuff), so just setting a browser to open full screen isn't enough. I guess that from that standpoint, It would be an idea to have some sort of basic menu/buttons which you can easily setup as an administrator and thats all the users get. But at the moment I got to work with what I got and with what I know.

Have you set up something similar?

Thanks for the tips.

---

### Post by lykwydchykyn on 2012-03-23
> **xris_xcess said:**
> Great tip!

I see what you mean by building up a tailored system, instead of adapting a current one.

I'm still a bit miffed at the fact that xfce's kiosk mode is documented and people have got it to work successfully... just not me!!!

The machines in question are to be used in a computer lab in a school. The idea is that each student has an account which they can access from any machine. Mainly from the storage point of view, so as to have access to whatever material they have in their home folder.

The difference with respect to just a web-kiosk, is that I will be offering a regular desktop experience and several other applications (openoffice, pdf viewer, video player, paint program and several other education stuff), so just setting a browser to open full screen isn't enough. I guess that from that standpoint, It would be an idea to have some sort of basic menu/buttons which you can easily setup as an administrator and thats all the users get. But at the moment I got to work with what I got and with what I know.

Have you set up something similar?

Thanks for the tips.

I've only set up the browser kiosks, but the main thrust was the whole copying over vs. locking-down idea.   Perhaps you could do something similar, and only copy over the XFCE configuration files.  Remember, everything user-specific is just a file in the user's home.  Restoring settings is just a matter of copying files.  It's never any more complicated than that.

But I wonder -- if each student has his/her own home folder, why go to a lot of trouble locking it down?  What are you wanting to prevent the student from doing, knowing that it will only affect him and nobody else?

---

### Post by xris_xcess on 2012-03-23
Well, overall, nothing really. It's more a question of keeping things tidy and funtional. Past experience has shown that if some users can change something, they will, even if they are not sure of what they are doing.

I guess I could start off with a standard basic setup and see how it goes. If users tend to break it up and are left with a non functional setup (ie, no panels), I can easily restore by copying over from the master files.

I guess it's trial time.

---

### Post by lykwydchykyn on 2012-03-24
I don't know how many systems and students you have, but that's probably going to be easier than worrying about locking every possible thing down.

You could get a simple "reset XFCE" script put together that just clears out all the XFCE dotfiles and copies in your defaults, to make things easier. You could even run it at login or logout if you want to enforce a certain layout/configuration.

---

### Post by xris_xcess on 2012-03-26
I see what you mean. I had been thinking about something like that.

Do you have any info on were login-logout scripts might get run?

Thanks a lot.

---

### Post by lykwydchykyn on 2012-03-26
My XFCE is a little rusty these days, but most environments respect scripts or .desktop files in ~/.config/autostart/

If you want to get fancy, you can create a custom .xsession or .xinitrc file (as I described in that blog entry) and use that instead of the default xfce session file:

```

#run commands at login:
some_command_which_must_complete_first 
some_other_command_that_runs_in_the_background &

#run XFCE
xfce-session

#run commands on logout.
command_to_run_on_logout


```

---

### Post by xris_xcess on 2012-03-26
Mmm... I've been looking at xfce's docs and searched around and it seems that there is no straight forward way of doing it.

I did find out that if you are login in through a login manager and running X, the /etc/X11/Xreset script runs. I saw a tip about putting your commands here. I tested it with a simple one and it works! I'm a bit concerned about errors though. If my extra commands don't finish cleanly it might halt the x server... I'll have to read up on bash and make sure that if the commands can't run properly, they just stop and exit, letting the server get ready for the next session.

---

### Post by lykwydchykyn on 2012-03-26
There are a lot of ways you can do it, but personally I'd stick to editing the session scripts in the home directory, rather than hack around in /etc/X11.  For one thing, an update could remove your changes, and for another, you'll be affecting every user on the system (including any admin user you've set up), not just the kiosk users (if that's an issue, might not be).

---

### Post by xris_xcess on 2012-03-26
I agree, but what if you have several users? Maybe a hundred?

Since ubuntu and debian seem to have programed general startup scripts for xsessions for all users, I would have to create a new one and copy it to every users folder (and probably to /etc/skel so that I don't forget when new users are created / home folders are created).

I think there is an /etc/X11/Xreset.d (or similar idea) folder that you can add your own scripts that does not get overwritten when updates come along.

I guess the commands could check if the user belongs to the admin group and skip the overwrite?

---

### Post by lykwydchykyn on 2012-03-26
> **xris_xcess said:**
> I agree, but what if you have several users? Maybe a hundred?

Since ubuntu and debian seem to have programed general startup scripts for xsessions for all users, I would have to create a new one and copy it to every users folder (and probably to /etc/skel so that I don't forget when new users are created / home folders are created).

I think there is an /etc/X11/Xreset.d (or similar idea) folder that you can add your own scripts that does not get overwritten when updates come along.

I guess the commands could check if the user belongs to the admin group and skip the overwrite?

I don't think anyone, by default, has a .xsession or .xinitrc script.  By default the display manager runs what is in the selected xsession script under /usr/share/xsessions.  A local session script is sort of an "override".

You could easily script deployment of this, if you know your way around BASH.  

Alternately, you could also write your custom .xsession script, put it somewhere in /usr/local, then change /usr/share/xsessions/XFCE.desktop (or whatever the file is called) to point to your custom script.

---

### Post by xris_xcess on 2012-03-28
Cool... this is of great help.

I think I will end up doing a mix of things.

- Set up a predefined panels and settings as defaults, so that newly created users get the config.

- Modify the session scripts so that the config is reset after every logout.

I have been experimenting with the above... and have run into some nasty problems. I must admit I haven't made it easy on myself: I started with xfce4 v.4.8 in ubuntu 11.10, gave up, tried with xfce4 v.4.6 on debian squeeze... and now back to ubuntu (after finding that squeeze didn't offer the packages that I needed-expected). As it turns out, there are some differences on how xfce4 .v4.6 vs 4.8 do their session-panels-configs stuff. I was running around in circles...

There are several tips on how to get a set config as a default, mainly setup one as a regular user and then copy it to the main folder (ie. /etc/xdg/xfce/...). Most users seem to claim success... but not me. I discovered that when you create your own (as a user), on some items there is a PATH variable set to your home folder. Well, this path gets set over to the other users as well, and so they get a unusable panel!!!

Interestingly, if I remove the variable form the files, it does not seem to have an effect and whats more, it gets re-set again at some point. 

It seems that the only "proper" way of doing it is to meddle with the original configs and create a proper template.

What a mess.

Thanks a lot. I think that I will be signing on to the xfce forums to pursue this config stuff.

---

### Post by xris_xcess on 2012-04-05
Finaly!!!

I have the setup that I was going for:

- Locked panels, custom menu and locked desktop. ie, "full control"

I must say that the documentation for xfce4 was not exactly clear, at least on what version (4.6 vs 4.8), about what method for locking was the proper one. As I said before, there was the kioskrc file and the xml channel property mentioned. It seems that v4.8 only respects/uses the xml-per-channel via.

One I got the hang of the config files (panels, menus, launchers, etc) it was quite simple.  The tricky bit is that the default config directory (/etc/xdg/xfce4/xfconf/xml-per-channel/) does not contain all the possible configuration files. So, ideally, you have to set up a user first with the settings that you wish to enforce, and then copy some of the settings from that users config files.

I must warn you though, because some config files seem to be tailored to each user when they first log in, such as the sessions file. It is different from the default file. The first time I replaced the default with the users version, I could no longer log in correctly. I had to make sure each file was similar first and then provide my selected settings.

Another notable example is the panels config, especially with launcher buttons. When you create a launcher as a user, xfce4 creates a particular config file and dir especially for that launcher. This setup can not be copied over as the default. You must set all your launchers and panel settings within the xfce4-panels.xml default setting file, otherwise the users panels will not know where to find the launchers.

The only drawback I see for the time being is that I had to eliminate the desktop functionality (no icons, trash, etc, only background). This was because I wanted to eliminate the right-click menu showing up and offering options to the users, such as desktop settings, which means that then they can activate the applications menu and then get access to all manner of settings. I know that I can actually modify the applications menu, but for the time being I'll see how the users cope.

I guess I should be writing up a how-to so that others might follow, instead of having to fish around for the info...

---

### Post by talkingtek on 2012-08-15
> **xris_xcess said:**
> Finaly!!!

I have the setup that I was going for:

- Locked panels, custom menu and locked desktop. ie, "full control"

I must say that the documentation for xfce4 was not exactly clear, at least on what version (4.6 vs 4.8), about what method for locking was the proper one. As I said before, there was the kioskrc file and the xml channel property mentioned. It seems that v4.8 only respects/uses the xml-per-channel via.

One I got the hang of the config files (panels, menus, launchers, etc) it was quite simple.  The tricky bit is that the default config directory (/etc/xdg/xfce4/xfconf/xml-per-channel/) does not contain all the possible configuration files. So, ideally, you have to set up a user first with the settings that you wish to enforce, and then copy some of the settings from that users config files.

I must warn you though, because some config files seem to be tailored to each user when they first log in, such as the sessions file. It is different from the default file. The first time I replaced the default with the users version, I could no longer log in correctly. I had to make sure each file was similar first and then provide my selected settings.

Another notable example is the panels config, especially with launcher buttons. When you create a launcher as a user, xfce4 creates a particular config file and dir especially for that launcher. This setup can not be copied over as the default. You must set all your launchers and panel settings within the xfce4-panels.xml default setting file, otherwise the users panels will not know where to find the launchers.

The only drawback I see for the time being is that I had to eliminate the desktop functionality (no icons, trash, etc, only background). This was because I wanted to eliminate the right-click menu showing up and offering options to the users, such as desktop settings, which means that then they can activate the applications menu and then get access to all manner of settings. I know that I can actually modify the applications menu, but for the time being I'll see how the users cope.

I guess I should be writing up a how-to so that others might follow, instead of having to fish around for the info...


Can you write a how instruction ro direct me to the right info?  I was looking into that too.  Can you share what you did?  Thank you.

---

