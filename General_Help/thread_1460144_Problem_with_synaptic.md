---
title: "Problem with synaptic"
date: 2010-04-22
forum: General Help
---

### Post by mikhail85 on 2010-04-22
Hello good day. 

I have a problem loading synaptic package manager and also when i access ubuntu software center i can't view either "get free software" or "installed software", i get a "busy" mouse pointer when i access software center. 

These are the error messages i get at synpatic: 

 >  E: Type 'n' is not known on line 1 in source list /etc/apt/sources.list.d/ubuntu-wine-ppa-karmic.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

I get also the message that says, "This usually means that your installed packages have unmet dependencies".

An unresolvable problem occurred while initializing the package information.
Please report this bug against the 'update-manager' package and include the following error message:
'E:Type 'n' is not known on line 1 in source list /etc/apt/sources.list.d/ubuntu-wine-ppa-karmic.list, E:The list of sources could not be read.' 

i was about to install the latest version of wine using their method of upgrade via terminal commands. i was going to do this because ORBIT DL MANAGER doesn't seem to run well on  my stable version of wine i got from the software center. Well because let's face it, download managers in ubuntu doesn't compare much in features, options, etc with windows based apps.

I'm a newbie at ubuntu and will much appreciate any help i can get to get this fixed, coz i don't want to reinstall ubuntu all over again. I have it on dual boot with windows 7 ultimate. 

I hope someone can help me.

 Is there something like a system restore in ubuntu just like it is in windows that whenever something bad happens, system restore is usually there to the rescue. 

Thanks

Mike

---

### Post by snowpine on 2010-04-22
Welcome to Ubuntu! You will find that (unlike in Windows) error messages in Ubuntu are actually very informative.

> **mikhail85 said:**
> 
E: Type 'n' is not known on line 1 in source list /etc/apt/sources.list.d/ubuntu-wine-ppa-karmic.list


This is telling us there's an error at line 1 of the file /etc/apt/sources.list.d/ubuntu-wine-ppa-karmic.list. Apparently there is a stray letter 'n' that doesn't belong there.

I happen to know this file does *not* exist in a standard install of Ubuntu. So you must have added this software source yourself, and made a mistake doing so. But that's okay!

The easiest way to get help on these forums is to post the contents of this file here so other users can help you. You can go to Applications->Accessories->Terminal and type:

```
cat /etc/apt/sources.list.d/ubuntu-wine-ppa-karmic.list
```

Then copy and paste the output here so we can see what's in the file and try and help you. Hint: if you use "code" tags (look for the # button in the formatting options above where you type your post) it will format it easier to read.

ps As a beginner, it might be easier for you to find a Linux download manager that meets your needs than to install unstable and untested software to try and run non-native Windows applications... just a tip from a long-time user. :)

---

### Post by mikhail85 on 2010-04-22
Thank you Sir Snowpine for your help.

Ok, so i went into terminal and pasted the code u gave me and what i get below the code is the letter "n". 

```
michael@michael-desktop:~$ cat /etc/apt/sources.list.d/ubuntu-wine-ppa-karmic.list
n
```

I'm a total newbie at this one, yes i agree with you that linux is very informative and so far i'm enjoying it's features. I really hope that developers of gnome apps/software will make their programs more alike to windows apps, what i mean is, i hope they could add a GUI interface when installin (not that it really matters but would be cool that it can let you decide what fetures of the program you only want to install) and more features because some of the apps are just to simple and some features are left out like for example, shutting down the computer when a task is finished because sometimes i leave the house with my computer still running and i don't want to let my computer run til i get home when it has already finished it's task. :)

hope the code above helps. 

Thank you.

Will wait for further instructions. :popcorn:

Michael

---

### Post by snowpine on 2010-04-23
Hi Michael, your file only contains the letter 'n'. I am not sure why you did this, and my recommendation is to simply delete the file (COPY & PASTE this command so you do not accidentally make any typos; any command starting with "sudo" is potentially dangerous!):

```
sudo rm /etc/apt/sources.list.d/ubuntu-wine-ppa-karmic.list
```

and install the stable version of wine from the Ubuntu repository:

```
sudo apt-get update && sudo apt-get install wine
```

I would recommend that you hold off on editing important system files or installing unstable software until you know your way around Ubuntu a bit better. 

If you are looking for a "GUI interface when installin" check out the Ubuntu Software Center. Good luck! :)

---

### Post by 3rdalbum on 2010-04-23
I think Wine operates their own repository for Ubuntu, so you could try adding that. [www.winehq.org](www.winehq.org) should have the details.

---

### Post by mikhail85 on 2010-04-23
Wow! Thank you sir snowpine! You saved my system from being unusable in some areas, like Ubuntu software manager, synaptic, and computer janitor! Now it's all working again! Thank YOU! :KS

i don't really know what happened that an "n" got in the way. what i was doing back last night was following instructions from [HTML]http://www.winehq.org/download/deb[/HTML]. 

problem started when i pasted one of the given lines to software sources. i must've pressed a wrong key by mistake, especially that i am kinda used to using windows keyboard shortcuts. 

I kinda thought about it, I'll uninstall wine later. It didn't run any of the windows programs i wanted, they didn't run as they would in windows 7. i guess i'll boot back to windows whenever i need those programs badly.

Thank you so much for your help! :) :guitar:

---

