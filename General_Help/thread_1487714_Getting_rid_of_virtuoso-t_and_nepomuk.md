---
title: "Getting rid of virtuoso-t and nepomuk"
date: 2010-05-19
forum: General Help
---

### Post by Zeemvel on 2010-05-19
Hi,

No matter what desktop I use, there are 5 nepomuk processes and one virtuoso-t process running, taking up quite a lot of CPU in total.

These stupid things have been ruining my Ubuntu and KDE experience ever since I upgraded to 10.4.

I want to have those things NEVER run again, no matter what they're for, preferably by editing a config file because using graphical settings in KDE hasn't actually disabled them.

How can I do that?

Thanks.

EDIT: If I kill the process nepomukservices, it keeps coming back! Who does that??? I installed KDE 3.5 now (instead of the very bad KDE 4). I have no setting to disable desktop search, because the brilliant and good KDE 3.5 has no such useless, CPU hogging, feature. But somehow the evil KDE 4 still manages to hog down my system by keeping to spawn this nepomukservices process all the time even when I'm not logged into KDE4 at all! So... how do I DESTROY this nepomuk? Thanks.

---

### Post by leneflower on 2010-05-19
In the system settings, under "Advanced", is the "Desktop Search" option. You can turn off "Enable Nepomuk Semantic Desktop" there. That should get rid of those hogs ;-)

---

### Post by Zeemvel on 2010-05-19
> **leneflower said:**
> In the system settings, under "Advanced", is the "Desktop Search" option. You can turn off "Enable Nepomuk Semantic Desktop" there. That should get rid of those hogs ;-)

There isn't such a setting in KDE 3.5.11 Trinity...

Is there any cron file or startup file or whatever that starts these nepomuk processes? I have no idea where these config files are in Ubuntu, if anyone knows what file I can edit to stop auto starting of nepomuk and virtuoso, please let me know.

Also, when in KDE4, I already had disabled that exact setting! And yet there were today one virtuoso-t, one nepomukserver, and 6 (That's SIX!) nepomukservices processes running!!

---

### Post by jwbales on 2010-05-19
I'm running gnome, not KDE and right now nepomukservices, virtuoso-t and some process called backend are using 190% of my two cpus. If I kill the processes they just come back the next time I log in. Would love to yank these processes out by their roots if I could figure out how. This all started when I upgraded to 10.04.

---

### Post by jwbales on 2010-05-19
Well, I had a simple 'duh' solution. I did a complete removal of virtuoso-nepomuk in Synaptic Package Manager.

Now when I log in a window pops up and scolds "Nepomuk Semantic Desktop needs the virtuoso RDF server to store its data. Installing the virtuoso soprano plugin is mandatory for using Nepomuk." To which I give a well-deserved rasberry.

Evidently the Nepomuk Semantic Desktop is not ready for prime time. When they get the bugs out, maybe I'll consider using it.

---

### Post by freacert on 2010-05-30
> **jwbales said:**
> 

Now when I log in a window pops up and scolds "Nepomuk Semantic Desktop needs the virtuoso RDF server to store its data. Installing the virtuoso soprano plugin is mandatory for using Nepomuk." To which I give a well-deserved rasberry.
  

same problem here, think for deinstalling the nepomuk, we need to deinstall the python-kde4 package. Which i need for Kmail. (lovely mail program)

How to get rid of nepomuk???

---

### Post by mark@qtrac.eu on 2010-06-09
I have exactly the same problem: I use Kmail but don't want Nepomuk. I have reported this as a bug:
[https://bugs.launchpad.net/ubuntu/+source/kde4libs/+bug/591598](https://bugs.launchpad.net/ubuntu/+source/kde4libs/+bug/591598)
You can go to the bug's page and click the "This bug affects you" link since that might encourage Canonical to take it seriously.

Well it got downgraded to a "Question" rather than a bug. Anyway, I've come up with a solution that works for me:
[https://answers.launchpad.net/ubuntu/+source/kde4libs/+question/114281](https://answers.launchpad.net/ubuntu/+source/kde4libs/+question/114281)

---

### Post by Mikorist on 2011-05-13
> **Zeemvel said:**
> There isn't such a setting in KDE 3.5.11 Trinity...

Is there any cron file or startup file or whatever that starts these nepomuk processes? I have no idea where these config files are in Ubuntu, if anyone knows what file I can edit to stop auto starting of nepomuk and virtuoso, please let me know.

Also, when in KDE4, I already had disabled that exact setting! And yet there were today one virtuoso-t, one nepomukserver, and 6 (That's SIX!) nepomukservices processes running!!


```


killall nepomukserver
mkdir -p /usr/share/autostart/disabled


sudo mv -f /usr/share/autostart/nepomukserver.desktop /usr/share/autostart/disabled 2> /dev/null
sudo mv -f /usr/bin/nepomuk-rcgen /usr/bin/nepomuk-rcgen-x 2> /dev/null
sudo mv -f /usr/bin/nepomukserver /usr/bin/nepomukserver-x 2> /dev/null
sudo mv -f /usr/bin/nepomukservicestub /usr/bin/nepomukservicestub-x 2> /dev/null
chmod ugo-x /usr/bin/nepomuk*


```

---

