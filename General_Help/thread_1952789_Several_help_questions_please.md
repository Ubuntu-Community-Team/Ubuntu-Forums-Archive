---
title: "Several help questions please"
date: 2012-04-05
forum: General Help
---

### Post by clonezonedude on 2012-04-05
Hi community:

I know im not active here, but tonight I need your help please :(

I am having several issues, and I consider myself a noob, as I don't exploit my OS much, because I mostly use the web, however, the following issues have arisen

I apologize if my images are huge, IDK how to resize here

Updates:
Everytime I update anything, I get a fail message even if the update was successful

[img]http://fc01.deviantart.net/fs70/f/2012/095/d/2/issues_6__by_danielsard-d4v5do6.png[/IMG]
[IMG]http://fc00.deviantart.net/fs71/i/2012/095/c/7/issues_5__by_danielsard-d4v5do4.png[/IMG]
[IMG]http://fc00.deviantart.net/fs71/i/2012/095/5/7/issues_4__by_danielsard-d4v5dmg.png[/IMG]
[IMG]http://fc02.deviantart.net/fs71/i/2012/095/7/b/issues_2_by_danielsard-d4v5dmc.png[/IMG]
[IMG]http://fc08.deviantart.net/fs71/i/2012/095/3/d/issues_1_by_danielsard-d4v5dlk.png[/IMG]
[IMG]http://fc03.deviantart.net/fs71/i/2012/095/4/c/issues__by_danielsard-d4v5dkz.png[/IMG]

Issue #2

My OS is tending to run a lot slower this days. I know this is too broad of a question, but where can I check to get something more specific please?

Issue #3

I tried to upgrade my OS today to 12.04 LTS, and the page says "To upgrade from Ubuntu 11.10 or Ubuntu 10.04 LTS on a desktop system, press Alt+F2 and type in "update-manager -d" (without the quotes) into the command box. Update Manager should open up and tell you: New distribution release '12.04' is available. Click Upgrade and follow the on-screen instructions."

All good until I do that, and no manager appears 

Last issue

I used to be able when I first installed 11.10 to drag a window to the side, and have it stick half size to whichever side I dragged it. I installed the cube visual, and eventually got bored, and got rid of it, but there went the ability to stick a window to the side. How can I get it back please?

Please help me. I know im NOT entitled to the help, and it is a _favor_ i'm asking. Experts, please be nice with me, im a super noob who wants to fix his OS to its former glory

Thanks a lot for all your help in advance :D

CZD

---

### Post by plucky on 2012-04-05
Open a terminal and post output between [noparse]```

```[/noparse] blocks for ```
sudo apt-get update
```

And if no errors,try ```
sudo apt-get install -f
``` and again post the output.

Good luck

---

### Post by clonezonedude on 2012-04-05
What do you mean output?

---

### Post by lisati on 2012-04-05
> **clonezonedude said:**
> What do you mean output?

When you run a command, it will produce its response on the screen. This response is known as "output."

---

### Post by Vaphell on 2012-04-05
you don't have to make pictures of terminal, you can copy/paste stuff by highlight-selecting/middle-clicking or ctrl+shift+c/ctrl+v (copy/paste in terminal require additional shift)
remember to put the text in [code][****/code] tags

---

### Post by cogier on 2012-04-05
The good people above are all correct but I suspect you may find their advice a little difficult to understand, and I apologise if that is not the case.

You need to open a Terminal session by pressing and holding down [Ctrl] & [Alt] and pressing "T". Then following plucky's sound advice type in the first command "sudo apt-get update". You will be asked for your password which is the same as the password you use to log in with, and or setup on installation. You will not see any cursor movement but if you type your password correctly all will be OK.

Repeat plucky's second command and type in the password as above if required (it may not be if you are fairly quick).

Hope that helps.

---

### Post by clonezonedude on 2012-04-05
**Vaphell**: sorry, for the massive screenshots :( . I will be using code tags for code from now on :) I honestly didnt mean to cause bother

**cogier**: Thanks, I really need to be translated that way while I learn my way. I honestly appreciate it, and I'm really thankful :)

**plucky**: I ran sudo apt-get update, and it ran pretty smoothly, except for this

```
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9A06AEF9CB8DB0

```

Should I keep going and go for the next step, or how do I get a public key please?

**lisati**: also thanks for explaining me about the output :)

Thanks so far for all the help I truly appreciate it :D , I really want to learn so I dont end up causing my Ubuntu OS to self destruct xDD

---

### Post by grahammechanical on 2012-04-05
We are assuming that you are still on 11.10. Open the Dash and type Software Sources and click on the icon. When the Dialogue opens you can click on the Other Software tab and look in the list.

You should see a line that starts with 

> [http://ppa.launchpad](http://ppa.launchpad)   There should be two lines like that.

Remove the check mark against both of them. Now if you run sudo apt-get update you will not get that error message and you can run the other command as well.

Also if you check this link:

[https://help.ubuntu.com/10.04/about-ubuntu/C/upgrade.html]("https://help.ubuntu.com/10.04/about-ubuntu/C/upgrade.html")

I think that you will find that the command that you ran to upgrade to 12.04 is not meant to load the Update Manager but to put an option in Update Manager to upgrade to 12.04.

Open Update Manager from the Dash by typing its name or from the power cog menu. It should be the 4th line down. and see if you now have a button tell you that an upgrade to 12.04 is available.

Regards.

---

### Post by clonezonedude on 2012-04-05
Thanks grahammechanical, I got rid of the checkmarks, and the update was successful. However, I went for the second command, but was hit by this not so pretty screen

```
update-alternatives: error: unable to make /usr/share/icons/gnome/16x16/places/start-here.png.dpkg-tmp a symlink to /etc/alternatives/start-here-16.png: No such file or directory
dpkg: error processing gnome-colors-common (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of gnome-brave-icon-theme:
 gnome-brave-icon-theme depends on gnome-colors-common; however:
  Package gnome-colors-common is not configured yet.
dpkg: error processing gnome-brave-icon-theme (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-dust-icon-theme:
 gnome-dust-icon-theme depends on gnome-colors-common; however:
  Package gnome-colors-common is not configured yet.
dpkg: error processing gnome-dust-icon-theme (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-human-icon-theme:
 gnome-human-icon-theme depends on gnome-colors-common; however:
  Package gnome-colors-common is not configured yet.
dpkg: error processing gnome-human-icon-theme (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-illustrious-icon-theme:
 gnome-illustrious-icon-theme dependNo apport report written because the error message indicates its a followup error from a previous failure.
                                                              No apport report written because the error message indicates its a followup error from a previous failure.
        No apport report written because MaxReports is reached already
                                                                      No apport report written because MaxReports is reached already
                                                    No apport report written because MaxReports is reached already
                                  No apport report written because MaxReports is reached already
                No apport report written because MaxReports is reached already
                                                                              No apport report written because MaxReports is reached already
                                                            No apport report written because MaxReports is reached already
                                          No apport report written because MaxReports is reached already
                        No apport report written because MaxReports is reached already
      No apport report written because MaxReports is reached already
                                                                    s on gnome-colors-common; however:
  Package gnome-colors-common is not configured yet.
dpkg: error processing gnome-illustrious-icon-theme (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-noble-icon-theme:
 gnome-noble-icon-theme depends on gnome-colors-common; however:
  Package gnome-colors-common is not configured yet.
dpkg: error processing gnome-noble-icon-theme (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-wine-icon-theme:
 gnome-wine-icon-theme depends on gnome-colors-common; however:
  Package gnome-colors-common is not configured yet.
dpkg: error processing gnome-wine-icon-theme (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-wise-icon-theme:
 gnome-wise-icon-theme depends on gnome-colors-common; however:
  Package gnome-colors-common is not configured yet.
dpkg: error processing gNo apport report written because MaxReports is reached already
      No apport report written because MaxReports is reached already
                                                                    No apport report written because MaxReports is reached already
                                                  No apport report written because MaxReports is reached already
                                nome-wise-icon-theme (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-colors:
 gnome-colors depends on gnome-brave-icon-theme; however:
  Package gnome-brave-icon-theme is not configured yet.
 gnome-colors depends on gnome-dust-icon-theme; however:
  Package gnome-dust-icon-theme is not configured yet.
 gnome-colors depends on gnome-human-icon-theme; however:
  Package gnome-human-icon-theme is not configured yet.
 gnome-colors depends on gnome-illustrious-icon-theme; however:
  Package gnome-illustrious-icon-theme is not configured yet.
 gnome-colors depends on gnome-noble-icon-theme; however:
  Package gnome-noble-icon-theme is not configured yet.
 gnome-colors depends on gnome-wine-icon-theme; however:
  Package gnome-wine-icon-theme is not configured yet.
 gnome-colors depends on gnome-wise-icon-theme; however:
  Package gnome-wise-icon-theme is not configured yet.
dpkg: error processing gnome-colors (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of shiki-brave-theme:
 shiki-brave-theme depends on gnome-brave-icon-theme; however:
  Package gnome-brave-icon-theme is not configured yet.
dpkg: error processing shiki-brave-theme (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of shiki-dust-theme:
 shiki-dust-theme depends on gnome-dust-icon-theme; however:
  Package gnome-dust-icon-theme is not configured yet.
dpkg: error processing shiki-dust-theme (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of shiki-human-theme:
 shiki-human-theme depends on gnome-human-icon-theme; however:
  Package gnome-human-icon-theme is not configured yet.
dpkg: error processing shiki-human-theme (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of shiki-illustrious-theme:
 shiki-illustrious-theme depends on gnome-illustrious-icon-theme; however:
  Package gnome-illustrious-icon-theme is not configured yet.
dpkg: error processing shiki-illustrious-theme (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of shiki-noble-theme:
 shiki-noble-theme depends on gnome-noble-icon-theme; however:
  Package gnome-noble-icon-theme is not configured yet.
dpkg: error processing shiki-noble-theme (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of shiki-wine-theme:
 shiki-wine-theme depends on gnome-wine-icon-theme; however:
  Package gnome-wine-icon-theme is not configured yet.
dpkg: error processing shiki-wine-theme (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of shiki-wise-theme:
 shiki-wise-theme depends on gnome-wise-icon-theme; however:
  Package gnome-wise-icon-theme is not configured yet.
dpkg: error processing shiki-wise-theme (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of shiki-colors:
 shiki-colors depends on shiki-brave-theme; however:
  Package shiki-brave-theme is not configured yet.
 shiki-colors depends on shiki-dust-theme; however:
  Package shiki-dust-theme is not configured yet.
 shiki-colors depends on shiki-human-theme; however:
  Package shiki-human-theme is not configured yet.
 shiki-colors depends on shiki-illustrious-theme; however:
  Package shiki-illustrious-theme is not configured yet.
 shiki-colors depends on shiki-noble-theme; however:
  Package shiki-noble-theme is not configured yet.
 shiki-colors depends on shiki-wine-theme; however:
  Package shiki-wine-theme is not configured yet.
 shiki-colors depends on shiki-wise-theme; however:
  Package shiki-wise-theme is not configured yet.
dpkg: error processing shiki-colors (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gnome-colors-common
 gnome-brave-icon-theme
 gnome-dust-icon-theme
 gnome-human-icon-theme
 gnome-illustrious-icon-theme
 gnome-noble-icon-theme
 gnome-wine-icon-theme
 gnome-wise-icon-theme
 gnome-colors
 shiki-brave-theme
 shiki-dust-theme
 shiki-human-theme
 shiki-illustrious-theme
 shiki-noble-theme
 shiki-wine-theme
 shiki-wise-theme
 shiki-colors
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

That is the same issue I keep getting time after time after I try to install/remove something

Says something about dependencies, but honestly it just confuses me more

What should I do in this case plz?

Plz let me know

Thanks a lot in advance :)

---

### Post by plucky on 2012-04-06
> dpkg: dependency problems prevent configuration of gnome-brave-icon-theme:
 gnome-brave-icon-theme depends on gnome-colors-common; however:
 **Package gnome-colors-common is not configured yet.**


What were you trying to install before the errors started happening?

You could try opening **Synaptic Package Manager** and try to fix broken Packages or install **gnome-colors-common** as that seems to be the dependancy that is missing.

```
sudo apt-get install gnome-colors-common
```

Good luck

---

### Post by clonezonedude on 2012-04-06
Thanks plucky, unfortunately I tried that and keep getting the same error

```
dpkg: error processing gnome-colors-common (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of gnome-brave-icon-theme:
 gnome-brave-icon-theme depends on gnome-colors-common; however:
  Package gnome-colors-common is not configured yet.
dpkg: error processing gnome-brave-icon-theme (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-dust-icon-theme:
 gnome-dust-icon-theme depends on gnome-colors-common; however:
  Package gnome-colors-common is not configured yet.
dpkg: error processing gnome-dust-icon-theme (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-human-icon-theme:
 gnome-human-icon-theme depends on gnome-colors-common; however:
  Package gnome-colors-common is not configured yet.
dpkg: error processing gnome-human-icon-theme (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-illustrious-icon-theme:
 gnome-illustrious-icon-theme dependNo apport report written because the error message indicates its a followup error from a previous failure.
                                                              No apport report written because the error message indicates its a followup error from a previous failure.
        No apport report written because MaxReports is reached already
                                                                      No apport report written because MaxReports is reached already
                                                    No apport report written because MaxReports is reached already
                                  No apport report written because MaxReports is reached already
                No apport report written because MaxReports is reached already
                                                                              No apport report written because MaxReports is reached already
                                                            No apport report written because MaxReports is reached already
                                          No apport report written because MaxReports is reached already
                        No apport report written because MaxReports is reached already
      No apport report written because MaxReports is reached already
                                                                    s on gnome-colors-common; however:
  Package gnome-colors-common is not configured yet.
dpkg: error processing gnome-illustrious-icon-theme (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-noble-icon-theme:
 gnome-noble-icon-theme depends on gnome-colors-common; however:
  Package gnome-colors-common is not configured yet.
dpkg: error processing gnome-noble-icon-theme (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-wine-icon-theme:
 gnome-wine-icon-theme depends on gnome-colors-common; however:
  Package gnome-colors-common is not configured yet.
dpkg: error processing gnome-wine-icon-theme (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-wise-icon-theme:
 gnome-wise-icon-theme depends on gnome-colors-common; however:
  Package gnome-colors-common is not configured yet.
dpkg: error processing gNo apport report written because MaxReports is reached already
      No apport report written because MaxReports is reached already
                                                                    No apport report written because MaxReports is reached already
                                                  No apport report written because MaxReports is reached already
                                nome-wise-icon-theme (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-colors:
 gnome-colors depends on gnome-brave-icon-theme; however:
  Package gnome-brave-icon-theme is not configured yet.
 gnome-colors depends on gnome-dust-icon-theme; however:
  Package gnome-dust-icon-theme is not configured yet.
 gnome-colors depends on gnome-human-icon-theme; however:
  Package gnome-human-icon-theme is not configured yet.
 gnome-colors depends on gnome-illustrious-icon-theme; however:
  Package gnome-illustrious-icon-theme is not configured yet.
 gnome-colors depends on gnome-noble-icon-theme; however:
  Package gnome-noble-icon-theme is not configured yet.
 gnome-colors depends on gnome-wine-icon-theme; however:
  Package gnome-wine-icon-theme is not configured yet.
 gnome-colors depends on gnome-wise-icon-theme; however:
  Package gnome-wise-icon-theme is not configured yet.
dpkg: error processing gnome-colors (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of shiki-brave-theme:
 shiki-brave-theme depends on gnome-brave-icon-theme; however:
  Package gnome-brave-icon-theme is not configured yet.
dpkg: error processing shiki-brave-theme (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of shiki-dust-theme:
 shiki-dust-theme depends on gnome-dust-icon-theme; however:
  Package gnome-dust-icon-theme is not configured yet.
dpkg: error processing shiki-dust-theme (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of shiki-human-theme:
 shiki-human-theme depends on gnome-human-icon-theme; however:
  Package gnome-human-icon-theme is not configured yet.
dpkg: error processing shiki-human-theme (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of shiki-illustrious-theme:
 shiki-illustrious-theme depends on gnome-illustrious-icon-theme; however:
  Package gnome-illustrious-icon-theme is not configured yet.
dpkg: error processing shiki-illustrious-theme (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of shiki-noble-theme:
 shiki-noble-theme depends on gnome-noble-icon-theme; however:
  Package gnome-noble-icon-theme is not configured yet.
dpkg: error processing shiki-noble-theme (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of shiki-wine-theme:
 shiki-wine-theme depends on gnome-wine-icon-theme; however:
  Package gnome-wine-icon-theme is not configured yet.
dpkg: error processing shiki-wine-theme (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of shiki-wise-theme:
 shiki-wise-theme depends on gnome-wise-icon-theme; however:
  Package gnome-wise-icon-theme is not configured yet.
dpkg: error processing shiki-wise-theme (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of shiki-colors:
 shiki-colors depends on shiki-brave-theme; however:
  Package shiki-brave-theme is not configured yet.
 shiki-colors depends on shiki-dust-theme; however:
  Package shiki-dust-theme is not configured yet.
 shiki-colors depends on shiki-human-theme; however:
  Package shiki-human-theme is not configured yet.
 shiki-colors depends on shiki-illustrious-theme; however:
  Package shiki-illustrious-theme is not configured yet.
 shiki-colors depends on shiki-noble-theme; however:
  Package shiki-noble-theme is not configured yet.
 shiki-colors depends on shiki-wine-theme; however:
  Package shiki-wine-theme is not configured yet.
 shiki-colors depends on shiki-wise-theme; however:
  Package shiki-wise-theme is not configured yet.
dpkg: error processing shiki-colors (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gnome-colors-common
 gnome-brave-icon-theme
 gnome-dust-icon-theme
 gnome-human-icon-theme
 gnome-illustrious-icon-theme
 gnome-noble-icon-theme
 gnome-wine-icon-theme
 gnome-wise-icon-theme
 gnome-colors
 shiki-brave-theme
 shiki-dust-theme
 shiki-human-theme
 shiki-illustrious-theme
 shiki-noble-theme
 shiki-wine-theme
 shiki-wise-theme
 shiki-colors
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I read something about wine, should I remove wine and try again? I'm starting to feel tempted to reformating my computer and starting fresh with 12.04 LTS. 

What do you think?

Plz let me know

Thanks

---

### Post by clonezonedude on 2012-04-08
bump please?

---

### Post by abyrne on 2012-04-08
Hi clonezone,

I just want to let you know that you shouldn't ever feel like you don't *deserve* help. Helping others is part of the Ubuntu experience, and we're all happy to do so. 

Anyway, you seem to have run into a bug in the gnome-colors-common package (cited [here]("https://answers.launchpad.net/ubuntu/+source/apt/+question/185577") and [here]("https://bugs.launchpad.net/ubuntu/+source/gnome-colors/+bug/922444")). If your bug is the same as others, then running the following commands might help.

```
sudo apt-get install gnome-icon-theme-full
```
Then run
```
sudo dpkg-reconfigure gnome-colors-common
```
Finally, run
```
sudo apt-get update
sudo apt-get upgrade
```

If any errors are given, please post the output.

---

### Post by clonezonedude on 2012-04-09
Hi abyrne

Thanks for offering me help :) The reason I said what I said is because of an article I read a few months ago that complained how windows users going toward ubuntu assumed that they were entitled to the help and were acting all rude and so(which I disagree, and hence said what I said, as I have been one of those once (a windows to Ubuntu user, not a rude one I hope xD ), and still my Ubuntu level of knowledge isn't yet too high)

I ran the commands you gave me, and there were two things that worried me a little

```
update-alternatives: warning: skip creation of /usr/share/icons/gnome/256x256/places/start-here.png because associated file /usr/share/icons/gnome/256x256/places/ubuntu-logo.png (of link group start-here.svg) doesn't exist.
update-alternatives: warning: skip creation of /usr/share/icons/gnome/48x48/places/start-here.png because associated file /usr/share/icons/gnome/48x48/places/ubuntu-logo.png (of link group start-here.svg) doesn't exist.
```

Am I missing an important system file?

Also when I ran this, 

```
danielsard@danielsard-M11x:~$ sudo dpkg-reconfigure gnome-colors-common
```

Ran it twice, and both times, the only output was

```
[code]danielsard@danielsard-M11x:~$
```

So IDK if the command was executed at all :(

Thanks so far for your valuable help :D you guys surely are an amazing community!! :D

---

### Post by abyrne on 2012-04-09
> Am I missing an important system file?
The file the command mentions is simply an icon file, specifically the Ubuntu logo that used to appear in the menu in older versions of Ubuntu.

> Ran it twice, and both times, the only output was...
That's fine; the command you ran simply "reset" the package that installs icon files. Since the package doesn't do anything particularly complex, no questions are asked and no output is given.

The commands that you should be concerned about are 
```
sudo apt-get update
sudo apt-get upgrade
```
For purely educational purposes, allow me to explain what the two above commands do. ***You can totally skip this paragraph if you're not interested.*** The first part of the command, "sudo", is mostly just a security feature that prevents unauthorized changes to your system; that's why it asks for your password. The next part of the command, "apt-get", is just the part of your system that does the "heavy lifting" for programs like Software Center, Update Manager, and Synaptic. It basically manages the applications installed on your system. The final part of the first command, "update", just makes sure that your "catalog" of software is up-to-date with the "catalog" that is maintained by the Ubuntu community. The final part of the second command, "upgrade" tells the system to scan through its own list of installed software and compare it to the list of software that was obtained in the first command. If there are newer versions of any programs available, then the system attempts to install them. That's where you ran into a problem. The gnome-colors software package (which simply provides icons for other applications) has a bug that causes its own upgrade process to fail if certain files don't exist. This causes a domino effect, causing the upgrade processes of many other software packages to fail. The "workaround" to your problem was to install the gnome-icon-theme-full software package, which provides the files that our gnome-colors package requires. This reverses the domino effect, allowing all of your software to upgrade successfully. 
(Don't worry if you didn't understand any of that; it's hard to learn how the entire apt package system in one paragraph)

_In other words, if the above two commands ran through successfully, then you're all good. Just to be sure, run both of the commands again and post all of the output._

*Also, as a note on that article you read,* there are more than a few Linux (Ubuntu is a variation of Linux) communities that are a lot less friendly to newcomers and beginners. A lot of people are stuck in the old ways of Linux, which used to be largely a "figure it out yourself" kind of project. However, Linux has grown far past those times, and Ubuntu is designed to be useful to both the common home user and the experienced IT administrator. And without getting too preachy (although I may be far past that point already), my favorite part of the Ubuntu project is probably the name, an African word meaning "I am what I am because of who we all are."

---

### Post by clonezonedude on 2012-04-16
abyrne thanks a lot!! :D seems like updates are working again. I cant believe something like icons could create so much trouble. I apologize I took so long to reply, as I've been having serious college stress that keep me from being more prompt

I hate to keep asking questions, but I seem not to be getting along with my copy of Ubuntu, as lately even with several updates and reboots, the system keeps getting slower and slower by times (pretty moody if you know what I mean), and also my computer (which is not overclocked, as I removed the option in purpose) heats up like there is no tomorrow (I use an Alienware m11x)

I am wondering if there is some sort of bad configuration or something I may have made as a big time noob I am

Finally, I have been trying to upgrade to Precise Pangolin with no success. I follow the first instruction

```
Upgrading from Ubuntu 11.10 or Ubuntu 10.04 LTS
To upgrade from Ubuntu 11.10 or Ubuntu 10.04 LTS on a desktop system, press Alt+F2 and type in "update-manager -d" (without the quotes) into the command box. Update Manager should open up and tell you: New distribution release '12.04' is available. Click Upgrade and follow the on-screen instructions.
```

I do Alt-F2, and type what says there, but nothing happens. I go to the regular update manager, and nothing either

If anybody could please shine me a light on what I'm doing wrong, it would be amazing :)

Please help me if you don't mind :redface:
Thanks a lot in advance 

CZD

---

### Post by clonezonedude on 2012-04-17
I hope I dont get too annoying for bumping this :X

---

### Post by plucky on 2012-04-18
Are you completely up to date with the updates?

Try running the ```
update-manager -d
``` command in a terminal window.

Does the update-manager window open and offer you the distribution upgrade?

Post output of terminal window if it doesn't.

Good Luck

---

### Post by clonezonedude on 2012-04-18
Wow thanks :D I started the upgrade, however I'm gonna hold on to the point of no return until I get home

I did get some errors however

```
(update-manager:6705): Gdk-CRITICAL **: gdk_window_get_pointer: assertion `GDK_IS_WINDOW (window)' failed

(update-manager:6705): Gdk-CRITICAL **: gdk_window_get_pointer: assertion `GDK_IS_WINDOW (window)' failed

(update-manager:6705): Gdk-CRITICAL **: gdk_window_get_pointer: assertion `GDK_IS_WINDOW (window)' failed

(update-manager:6705): Gdk-CRITICAL **: gdk_window_get_pointer: assertion `GDK_IS_WINDOW (window)' failed

(update-manager:6705): Gdk-CRITICAL **: gdk_window_get_pointer: assertion `GDK_IS_WINDOW (window)' failed

(update-manager:6705): Gdk-CRITICAL **: gdk_window_get_pointer: assertion `GDK_IS_WINDOW (window)' failed

(update-manager:6705): Gdk-CRITICAL **: gdk_window_get_pointer: assertion `GDK_IS_WINDOW (window)' failed

(update-manager:6705): Gdk-CRITICAL **: gdk_window_get_pointer: assertion `GDK_IS_WINDOW (window)' failed

(update-manager:6705): Gdk-CRITICAL **: gdk_window_get_pointer: assertion `GDK_IS_WINDOW (window)' failed

(update-manager:6705): Gdk-CRITICAL **: gdk_window_get_pointer: assertion `GDK_IS_WINDOW (window)' failed

(update-manager:6705): Gdk-CRITICAL **: gdk_window_get_pointer: assertion `GDK_IS_WINDOW (window)' failed
authenticate 'precise.tar.gz' against 'precise.tar.gz.gpg' 
extracting 'precise.tar.gz'
WARNING: Failed to read mirror file

```

I wonder if they are too bad, as I have no clue what they mean "gdk_window_get_pointer"?

Plz let me know

Thanks in advance and thanks for all the valuable help :D

---

### Post by abyrne on 2012-04-19
> 
```

(update-manager:6705): Gdk-CRITICAL **: gdk_window_get_pointer: assertion `GDK_IS_WINDOW (window)' failed

```

I wonder if they are too bad, as I have no clue what they mean "gdk_window_get_pointer"?



Whenever you start a graphical application via the terminal, it almost always spits out a lot of meaningless warnings and errors. These errors won't affect your upgrade process, and are completely harmless.

---

### Post by clonezonedude on 2012-04-22
I wanted to let everybody know that thanks to ALL of your help, I have now successfully upgraded to 12.04 and it runs like the smoothest silk!!

Thanks so much to everyone for your help!! you all rock!!! :D :D :D

---

