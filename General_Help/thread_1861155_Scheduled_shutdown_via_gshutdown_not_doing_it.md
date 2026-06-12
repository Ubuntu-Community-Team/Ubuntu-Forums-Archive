---
title: "Scheduled shutdown via gshutdown not doing it"
date: 2011-10-15
forum: General Help
---

### Post by Tornikee on 2011-10-15
Hello,

I searched for a shutdown scheduler soft for Ubuntu via the Software Center and found gshutdown, which seems to have all the necessary options for doing it, although every time the countdown set by me to shutting the Ubuntu down reaches 0, it logs off to the log in screen, instead of shutting down.
Is there any other similar software, or how can I correct this in gshutdown?

Thanks in advance.

---

### Post by Tornikee on 2011-10-17
Anything?

---

### Post by yoramdavid on 2011-12-06
> **Tornikee said:**
> Hello,

I searched for a shutdown scheduler soft for Ubuntu via the Software Center and found gshutdown, which seems to have all the necessary options for doing it, although every time the countdown set by me to shutting the Ubuntu down reaches 0, it logs off to the log in screen, instead of shutting down.
Is there any other similar software, or how can I correct this in gshutdown?

Thanks in advance.

Hi, I hope I am still on time to help.
You must change the settings of gshutdown as follows:
Edit-Preferences
Select customized command and under shutdown you should have the following:
shutdown -h now

to reboot:
reboot

to logoff:
/usr/bin/gnome-session-save --kill --silent

Also, select "execute a command before the action" and type:
nautilus -q

That should work.

---

### Post by Tornikee on 2011-12-06
Thanks a lot for the reply. Will reinstall gshutdown and follow your tips.

---

### Post by yoramdavid on 2011-12-06
> **Tornikee said:**
> Thanks a lot for the reply. Will reinstall gshutdown and follow your tips.

You are welcome.

I had the same problem a couple of years ago with Ubuntu 8 or 9, it got solved with the above solution.
I found that after upgrading to ubuntu 11.10, it did not even work with the above solution, it would just do nothing at all, so I solved the problem running gshutdwon as root by adding
gksu
before the shortcut to the application, using alacarte. It asks for you password to run the program.

---

### Post by Tornikee on 2011-12-08
I just tested this solution and it didn't work - the system didn't even log off after countdown ended. I guess I have a newer version of Gshutdown as some of the preferences are a bit different to those described by you, so I might have entered the commands in incorrect fields.
I've taken some screens:

[http://bit.ly/rzOAsf](http://bit.ly/rzOAsf)
[http://bit.ly/vqUDJz](http://bit.ly/vqUDJz)

Is this all correct?

---

### Post by yoramdavid on 2011-12-08
> **Tornikee said:**
> I just tested this solution and it didn't work - the system didn't even log off after countdown ended. I guess I have a newer version of Gshutdown as some of the preferences are a bit different to those described by you, so I might have entered the commands in incorrect fields.
I've taken some screens:

[http://bit.ly/rzOAsf](http://bit.ly/rzOAsf)
[http://bit.ly/vqUDJz](http://bit.ly/vqUDJz)

Is this all correct?

Your settings are correct. The screen-shots look the same as my program (version 0.2).

Please also run the following commands so the commands should not aks for a password:
```
sudo chmod +s /sbin/shutdown
```

and
```
sudo chmod +s /sbin/reboot
```

I had the same issue you have, it would do nothing even running these two commands as shutdown and reboot needs sudo.
That is why I added the 
```
gsku
``` in front of the link to the program to start it with sudo privileges.
My link to the program is like this now:
```
gksu /usr/bin/gshutdown
```

Do you know how to do this?

Yoram

---

### Post by Tornikee on 2011-12-08
Thanks for the reply.

I forgot how to make that adjustment, so a hint would be great.

---

### Post by yoramdavid on 2011-12-08
> **Tornikee said:**
> Thanks for the reply.

I forgot how to make that adjustment, so a hint would be great.

So, I am assuming it still did not work even running the two above commands?

I use a program you find in the ppa: "alacarte" which is a menu editor.
```
sudo apt-get install alacarte
```
So, install alacarte (you can reorganize all your menus the way you like with it) and browse for the shortcut to gshutdown, edit it and add the "gsku" bit to that menu entry.

---

### Post by Tornikee on 2011-12-08
Haven't tried those two commands yet. Should I just add them to 'nautilus -q' line?

---

### Post by yoramdavid on 2011-12-08
> **Tornikee said:**
> Haven't tried those two commands yet. Should I just add them to 'nautilus -q' line?

No, you run them in command line, one at a time. Then try gshutdown again.
If no luck try the solution with the "gsku" command using alacarte.

---

### Post by Tornikee on 2011-12-08
It worked after entering those two commands. Do I need to enter them each time before starting a GShutdown countdown?

---

### Post by yoramdavid on 2011-12-08
> **Tornikee said:**
> It worked after entering those two commands. Do I need to enter them each time before starting a GShutdown countdown?

I do not think so, that should be it. I think any way because it did not work for me.
Have you tried again?

---

### Post by Tornikee on 2011-12-08
Just did, and it worked. Thanks a lot for the assistance.

---

### Post by yoramdavid on 2011-12-08
> **Tornikee said:**
> Just did, and it worked. Thanks a lot for the assistance.

You are welcome, I am happy I could help someone!
Normally I am the one asking for help.

---

