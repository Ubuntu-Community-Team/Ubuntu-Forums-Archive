---
title: "User Login Screen - Question."
date: 2010-05-06
forum: General Help
---

### Post by Roasted on 2010-05-06
I rig my system up to be a file server (samba) with several users. As a result, those users appear at the login screen. I don't like that. I want one of two things:

A - The only user that comes up in the drop down list is me with the other users not listed.

B - Take away the drop down list of available users and be required to put in the username + password.

Ideas?

---

### Post by DomesDKG on 2010-05-06
Have you looked at System>Administration>Login Screen?

---

### Post by Flyers2391 on 2010-05-06
> **Roasted said:**
> 
B - Take away the drop down list of available users and be required to put in the username + password.

Ideas?

I've been looking for a way to to this since moving to Karmic but couldn't find it and gave up

---

### Post by Roasted on 2010-05-07
> **DomesDKG said:**
> Have you looked at System>Administration>Login Screen?

Yeah. The only options I get there are to auto login. I do not want auto login. I want it to be just like it is now, EXCEPT no other users listed (or no users listed at all).

---

### Post by StuartN on 2010-05-07
> **Roasted said:**
> I want it to be just like it is now, EXCEPT no other users listed (or no users listed at all).

I think you can use Applications -> System tools -> Configuration editor and then tick disable-user-list in apps/gdm/simple-greeter - but only if you are logged in as root or start **gconf-editor** with sudo (to change the root settings).

Open a terminal and type
```
sudo gconftool-2 --direct --config-source xml:readwrite:/etc/gconf/gconf.xml.defaults \
--type bool --set /apps/gdm/simple-greeter/disable_user_list true
```

Replace "true" with "false" to go back to displaying your user list.

---

### Post by Flyers2391 on 2010-05-07
> **StuartN said:**
> I think you can use Applications -> System tools -> Configuration editor and then tick disable-user-list in apps/gdm/simple-greeter - but only if you are logged in as root or start **gconf-editor** with sudo (to change the root settings).

Open a terminal and type
```
sudo gconftool-2 --direct --config-source xml:readwrite:/etc/gconf/gconf.xml.defaults \
--type bool --set /apps/gdm/simple-greeter/disable_user_list true
```

Replace "true" with "false" to go back to displaying your user list.

I went into the terminal, did gksudo gconf-editor (whose list is different than the one launching as a user), went to apps > gdm > simple-greeter and checked "disable_user_list".  Logged out and it still shows my name, restarted - no change.  OP, did this work for you?

---

### Post by pfnorris on 2010-05-07
> **Flyers2391 said:**
> I went into the terminal, did gksudo gconf-editor (whose list is different than the one launching as a user), went to apps > gdm > simple-greeter and checked "disable_user_list".  Logged out and it still shows my name, restarted - no change.  OP, did this work for you?

Once you have set that entry up in gconf-editor, right click it and select the 'set as default' command on the context menu.

Another option is to install ubuntu-tweak. This is a really handy tool that allows you to 'tweak' loads of settings via an easy to use gui. There is a section called 'login settings' where you can adjust this setting.

---

### Post by Hangwire on 2010-05-07
I may be getting a little over my head with this but how about just stop gdm from starting? 

we would do

```
mv /etc/init/gdm.conf /etc/init/gdm.disabled
```

On restart you will be prompted for your username and password, nothing else visible than a command line... 

When you want to start the GUI, just do 

```
startx
```

Well? :KS

---

### Post by Flyers2391 on 2010-05-07
> **pfnorris said:**
> Once you have set that entry up in gconf-editor, right click it and select the 'set as default' command on the context menu.

Set as default, that was what I needed, thanks!  Now I just need to work on getting num lock on at this screen ... it turns on after I login but I have to do it manually at the login screen.

---

### Post by Flyers2391 on 2010-05-07
> **Hangwire said:**
> I may be getting a little over my head with this but how about just stop gdm from starting? 

we would do

```
mv /etc/init/gdm.conf /etc/init/gdm.disabled
```

On restart you will be prompted for your username and password, nothing else visible than a command line... 

When you want to start the GUI, just do 

```
startx
```

Well? :KS

That actually answers a completely different question I couldn't find an answer to a while back ... and that was how to NOT start the gui on boot.  I will have to remember that in the future, thanks! :)

---

### Post by sisco311 on 2010-05-07
> **Roasted said:**
> 
A - The only user that comes up in the drop down list is me with the other users not listed.

Set the uid of the other users to be less than 1000.

> **Roasted said:**
> 
B - Take away the drop down list of available users and be required to put in the username + password.


You have to edit the gconf key as user gdm, not as root:
```
sudo -u gdm gconftool-2 --type bool --set /apps/gdm/simple-greeter/disable_user_list true
```

---

