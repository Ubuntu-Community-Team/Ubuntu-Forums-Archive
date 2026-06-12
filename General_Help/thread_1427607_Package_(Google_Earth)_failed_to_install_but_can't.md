---
title: "Package (Google Earth) failed to install but can't be removed or reinstalled"
date: 2010-03-11
forum: General Help
---

### Post by RobHK on 2010-03-11
I tried to install Google Earth, but it stuck at the EULA and I couldn't accept it. I couldn't close the window and had to shut down with it open.

Now I can't remove GE. I get the message: "E: googleearth: Package is in a very bad inconsistent state - you should  reinstall it before attempting a removal.", but I can't reinstall it either. The option is greyed out in the right-click menu.

---

### Post by audiomick on 2010-03-11
How are you trying to re-install? If you go to
system> administration> synaptics package manager
can you select it to re-install?
Use the search function to search "googleearth" to find it.

---

### Post by RobHK on 2010-03-11
> **audiomick said:**
> How are you trying to re-install? If you go to
system> administration> synaptics package manager
can you select it to re-install?
Use the search function to search "googleearth" to find it.
That's exactly what I'm trying to do. But the install option is greyed out. And it's worse than I thought,  because if I install something else, Synaptic still thinks it's supposed to be installing GE, and I get stuck again.

Please reply, but I won't see it till tomorrow as it's midnight where I am and I have to go to bed. Sorry :)

---

### Post by audiomick on 2010-03-11
Ok. It is 1:45 a.m. here. I should be in bed too...;)

I tried this, after reading
```
man apt-get
```on my system. Google earth still works, and the computer didn't blow up...
```
sudo apt-get install --reinstall googleearth
```The "sudo" means "do this with root privileges"
The "apt-get" is more or less the same thing as synaptic, but without the GUI
"install" is obvious, and the "--reinstall" option tells it to install even when the latest version is installed.

I don't know for sure that this will work, but I think there is a good chance.

edit: in case you haven't used "sudo" before: you will be asked for a password. Type in the password that you log on with. You wont see what you are typing. Hit enter to continue.

---

### Post by RobHK on 2010-03-12
> **audiomick said:**
> Ok. It is 1:45 a.m. here. I should be in bed too...;)

I tried this, after reading
```
man apt-get
```on my system. Google earth still works, and the computer didn't blow up...
```
sudo apt-get install --reinstall googleearth
```The "sudo" means "do this with root privileges"
The "apt-get" is more or less the same thing as synaptic, but without the GUI
"install" is obvious, and the "--reinstall" option tells it to install even when the latest version is installed.

I don't know for sure that this will work, but I think there is a good chance.

edit: in case you haven't used "sudo" before: you will be asked for a password. Type in the password that you log on with. You wont see what you are typing. Hit enter to continue.
Thanks. Michael. As you say, it was worth a try. Initially I got an error message about dpkg but I followed the instructions and was then able to reinstall google earth. But it stuck at the EULA again, and will not respond to any attempt to accept the EULA.

I looked at man apt-get and decided to try "purge" but I ran up against the EULA again. I've installed GE in Linux before, and I'm pretty sure I had to Click on "OK", but here it's impossible, I don't get a cursor, and there is no response to "Enter".

I guess I'll have to reinstall the system and forget about GE. It's not such a big disaster, as I only installed it yesterday. Just hope I can remember how my tweaks worked,

Thanks for your kind efforts. :)

---

