---
title: "Changed Home directory, now locked out"
date: 2009-08-28
forum: General Help
---

### Post by Ummsayyidah on 2009-08-28
Hiya, 

I am newish to Ubuntu and not really messed around with it much. 

Yesterday I tried to change the username on my second hand Dell netbook but it wouldnt let me. So I changed the name on the home directory to mine. 

Unfortunately no warning signs or bells went off when I dd this so I carried on. 

So now I'm locked out of my laptop! It says it cant find home directory (my name here)

Any help is appreciated and I hope this is in the right forum.

Ummsayyidah

---

### Post by ZekeDragon on 2009-08-28
Are you incapable of logging in at all, or does it report a problem elsewhere?

---

### Post by ronparent on 2009-08-28
Your best bet would have been to add yourself as a new user with all priviledges. The /home directory must not only have the same name as the user, but, must also be owned by that user. You might try changing the name of that directory back exactly to the one initially. If ownership has been altered, you still won't be able to boot and you will have to boot to the recovery mode to change ownership. To do this drop to a root prompt and enter commands as follows:

[B]chown -R username:username /home/username
chmod 644 /home/username/.dmrc
chmod 644 /home/username/.ICEauthority
exit[/B]

'username' will be the name of the original user. This series of commands will not be necessary if the system boots to the original users desktop once the /home directory name has been restored.

Once you are back into the desktop, go to System>Administration>User Accounts and add yourself as a user and set a password. From then on you will be able to access in your own name. If you want to recover configuration or data from the old user, you can then copy everything from the olduser to newuser account. You would probable then have to run the above routines at root prompt to change ownerships to give newuser access to read and write everything copied.

---

### Post by packit0 on 2011-02-03
Hi all,

I think I'm on a simmilar situation. I changed my username WHILE logged on and now despite being able to login nothing is visible on my desktop! I know I messed up completelly and should only change the username through a different user account. ](*,)

Anyway, I can only login with the NEW username, but I a get a series of warnings saying that Nautilus is unable to access the home folder for the OLD username (apparently I need to recreate manually?!) and in the end all I can see is the desktop image - no menu, mount points, nothing.

This is a brand new installation (dual boot with Windows XP) so I would not mind to reinstall it again if I have to. However, I suppose there's a way to recover from this situation from the command line? That way I could learn a bit more ;)

Please advise. Thanks!

---

### Post by nothingspecial on 2011-02-03
Try changing it back.

Reboot

hold down shift and choose root recovery shell or whatever they call it atm

type ```
usermod -l *previous_working_user* *current_broken_user*
```

Then type ```
exit
``` and see if you can login

---

### Post by packit0 on 2011-02-03
I'm "stuck" at work now but will definitelly give it a try later.

Thanks!

---

### Post by packit0 on 2011-02-03
Nope, it din't work! I still got the same error messages:

> 
Could not update ICEauthority file /home/<old working user>/.ICEauthority
then 
> 
There is a problem with the configuration server.
(/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256)
and finally...
> 
Nautilus could not create the following required  folders:/home/<old_working_user>/Desktop,  /home/<old_working_user>/.nautilus

Before runing Nautilus, please create these folders, or set permissions such as Nautilus can create them
 Any more suggestions anyone?

---

### Post by packit0 on 2011-02-03
I found a few posts for the error messages I was getting. Interesting stuff, but it's too late 'cos I've just started a new installation, using the same partitions... and this time with the correct usernames :)

---

