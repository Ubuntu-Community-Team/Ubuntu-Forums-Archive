---
title: "installing virtual box Kernel driver not installed (rc=-1908)"
date: 2011-10-25
forum: General Help
---

### Post by shining_shank on 2011-10-25
I am currently trying to install windows so I can use a site that it is only compatible with internet explorer. I have read and tried all the other posts related with the same error that I have been receiving.

These are the following commands that I have ran in terminal and in parentheses is the response:

sudo aptitude update (sudo: aptitude: command not found)
sudo aptitude install dkms (sudo: aptitude: command not found)
sudo /etc/init.d/vboxdrv setup (no msg received)
sudo /etc/init.d/vboxdrv.dpkg-bak setup (no msg received)
sudo /etc/init.d/whatever-it-is-in-yours restart (sudo: /etc/init.d/whatever-it-is-in-yours: command not found)
sudo /etc/init.d/virtualbox-ose restart (* Stopping VirtualBox kernel modules                                    [ OK ] 
 * Starting VirtualBox kernel modules                                            * No suitable module for running kernel found
                                                                         [fail])

I would gladly accept any advise,
Thanks in advance, shining_shank

---

### Post by searchfgold6789 on 2011-10-25
**[COLOR=Red]Wrong:[/COLOR]**```
sudo aptitude update
sudo aptitude install dkms
```**[COLOR=YellowGreen]Right:[/COLOR]**```
sudo apt-get update
sudo apt-get install dkms
```([SIZE=1]DKMS should be installed by default.[/SIZE])
I don't know what the other messages are. Did you install virtualbox-ose from the [debs on their website]("https://www.virtualbox.org/wiki/Linux_Downloads")? It was really easy for me; I didn't have to use the terminal at all.
 - search

---

