---
title: "Editing menus"
date: 2009-07-17
forum: General Help
---

### Post by Chris62 on 2009-07-17
Hi,

I have removed Evolution from my Ubuntu 9.04 system and have removed the icon from the launcher panel but when I click on "Office" in "Applications" there is still an entry for Evolution. Is there a way of removing this?

Also, whenever I run Update Manager it notifies me of updates for Evolution. Is there a way of stopping this so that I don't have to go through the list of things available for download, un-ticking (i.e. unchecking) all the ones pertaining to Evolution?

When I removed it, I used Synaptic and asked it to do a complete removal. I would have thought that it could/should have put some sort of flag saying "Evolution not wanted here" or something like that.

---

### Post by drs305 on 2009-07-17
Right click on the Ubuntu menu icon, select Edit. In the left pane, highlight Office and in the right pane highlight Evolution and select "Remove".

You could try running the following to see if it stops the Evolution messages, but I don't know if it will if Evolution is too basic to the installation. [COLOR="DarkRed"]Note some users have had problems when removing Evolution. This command will remove Evolution but not evolution-common or evolution-data-server-common, which may be used by other system resources. [/COLOR]:
```

sudo apt-get purge evolution

```

---

### Post by Chris62 on 2009-07-17
Many thanks drs305, 

I have done that and have no longer got the menu entry but I am a bit wary of doing your second suggestion. When I first tried to remove Evolution, having only just started using Ubuntu and being totally new to anything Linux, I removed every reference to Evolution and ended up with a machine which would only boot up into a command line. I don't want that to happen again because when it happened before I had to re-install Ubuntu. I understand that some "bits" of evolution are required for other packages. 

I can see why you are an Ubuntu addict. It is great compared with Window$ once one begins to get the hang of things. I was trying out Window$ 7 recently and it is just so cluttered up with options I hadn't asked for or wanted.

---

### Post by drs305 on 2009-07-17
I have run the command as posted and rebooted without any ill effects. The Evolution package is showing uninstalled in Synaptic although a couple of Evolution-related packages remain. I use Thunderbird as my email program and it is working fine.

You should always understand what a command will do and if you ever have questions ask for clarification or await others inputs. I will mark the command as having caused some users problems.

---

