---
title: "Ubuntu 11.10 64bit How To Install Nvidia Driver Version 290.20"
date: 2012-03-15
forum: General Help
---

### Post by AgentZ86 on 2012-03-15
Hi

Ubuntu 11.10 64bit How To Install Nvidia Driver Version 290.20
I saw things about updating the repositories to

ppa:ubuntu-x-swat/x-updates

[http://www.noobslab.com/2011/09/nvidia-drivers-for-ubuntu-1110-oneiric.html](http://www.noobslab.com/2011/09/nvidia-drivers-for-ubuntu-1110-oneiric.html)


But I actually did this from the software settings and added it

But even so it didn't update anything should I actually do whats listed here or shouldn't I simply be able to add this to the software center / settings and update the repositories

I also updated in synaptic and there were a lot of things added, however not 290.20 or nothing past 280 version

Please advise how I should install this driver

The reason is because there appears to be bugs in the 280 version which causes freezes and mouse issues for OpenGl applications which is the problem I'm also having and it's noted fixes in this new driver

Please advise


P.S
Nvidia latest driver for me here:
[http://www.nvidia.com/object/linux-display-amd64-295.20-driver.html](http://www.nvidia.com/object/linux-display-amd64-295.20-driver.html)




Thanks

---

### Post by tuX9th on 2012-03-15
If you want the latest driver just uninstall all the ubuntu packages and install the driver from the nvidia page.
though i wouldn't recommend that because you get no updates and its not supported by the ubuntu community.

about the ppa. did you follow the steps in this tutorial 
```
[COLOR=Black][COLOR=red]sudo apt-add-repository ppa:ubuntu-x-swat/x-updates[/COLOR][COLOR=red]
sudo apt-get update
sudo apt-get install nvidia-current[/COLOR][/COLOR]
```for me it works and adds the version 295.x.x

greets

---

### Post by AgentZ86 on 2012-03-15
> **tuX9th said:**
> If you want the latest driver just uninstall all the ubuntu packages and install the driver from the nvidia page.
though i wouldn't recommend that because you get no updates and its not supported by the ubuntu community.

about the ppa. did you follow the steps in this tutorial 
```
[COLOR=Black][COLOR=red]sudo apt-add-repository ppa:ubuntu-x-swat/x-updates[/COLOR][COLOR=red]
sudo apt-get update
sudo apt-get install nvidia-current[/COLOR][/COLOR]
```for me it works and adds the version 295.x.x

greets

Thanks for the response

When you say uninstall the ubuntu packages ? Can you clarify this please.

I am aware it's not supported unfortunatly the techs at several gaming sites suggests to update to the latest version which solves the bugs related to freezes and mouse issues for OpenGL applications etc.

I don't really want to either but not sure what else to try.

Anyhow, thanks again and please clarify the subject or uninstalling the ubuntu packages ? Which ones ? 

Thanks

---

### Post by tuX9th on 2012-03-15
nvidia-current
then install the driver you downloaded. and follow the instructions there.
if you don't have a graphics driver installed you'll have difficulties starting the window manager so keep in mind to check every step or else you'll be stuck in console only.

still, whats the problem with the ppa?

---

### Post by AgentZ86 on 2012-03-15
> **tuX9th said:**
> nvidia-current
then install the driver you downloaded. and follow the instructions there.
if you don't have a graphics driver installed you'll have difficulties starting the window manager so keep in mind to check every step or else you'll be stuck in console only.

still, whats the problem with the ppa?

Thanks for the reply

The current nvidia driver in stalled is (current) version 280.13 and thats what came with Ubuntu 11.10 to my knowledge

But the gameing sites are indicating a bug which causes various issues with OpenGl applications sometimes, and so the version 295.20 on the nvidia site specifically says this version fixes that and the gaming sites indicate the same.

But I do not know if there is any problem with the ppa I've not tried the exact method mentioned here yet because I wanted to make sure I understand what I'm doing and what not to do.

I tried to use the ubuntu default method such as add the ppa to the software center / settings / other software

And then went to system settings / additional hardware and attempted to let jockey find a new version or something but thats a no go

I also opened synaptic to see if I could actually see the versions listed but I didn't
I reloaded the packages and didn't see any upgraded driver versions listed

So I just wanted to understand what I was looking at before just installing something with apt. and wanted to see the dependencies etc. if I could

Anyhow so I should uninstalled nvidia-current

But then I thought the ppa would download install the latest driver should I download the driver from the nvidia site ? 

What am I missing here ?

Thanks

---

### Post by tuX9th on 2012-03-15
oh boy...
Just follow the steps i posted above to get it installed form the ppa
the first command adds the ppa as a repository to the APT
the second command reloads the lists of the repo
and the third command will download the driver.

if you can't deal with installing a ppa you really shouldn't try to install the nvidia driver manually. you'll end up with no graphic driver whatsoever


[COLOR=Black]```
[/COLOR][COLOR=Black][COLOR=red]sudo apt-add-repository ppa:ubuntu-x-swat/x-update[/COLOR][COLOR=red]
sudo apt-get update 
sudo apt-get install nvidia-current[/COLOR]
```
[/COLOR]if you want to know what you are doing read 
apt-add-repository -h
and apt-get

greets

---

### Post by AgentZ86 on 2012-03-15
> **tuX9th said:**
> oh boy...
Just follow the steps i posted above to get it installed form the ppa
the first command adds the ppa as a repository to the APT
the second command reloads the lists of the repo
and the third command will download the driver.

if you can't deal with installing a ppa you really shouldn't try to install the nvidia driver manually. you'll end up with no graphic driver whatsoever


[COLOR=Black]```
[/COLOR][COLOR=Black][COLOR=red]sudo apt-add-repository ppa:ubuntu-x-swat/x-update[/COLOR][COLOR=red]
sudo apt-get update 
sudo apt-get install nvidia-current[/COLOR]
```
[/COLOR]if you want to know what you are doing read 
apt-add-repository -h
and apt-get

greets

Ok thanks

I'll read that thanks, I've mostly used the synaptic to add repositories and read the dependencies and also history features if I messed something up

I didn't have any problems doing that so never used apt for anything really.

But guess it's time to read some of this, thanks

---

### Post by AgentZ86 on 2012-03-15
From this command:
sudo apt-add-repository ppa:ubuntu-x-swat/x-update

First thing I get is this in the terminal:


Traceback (most recent call last):
  File "/usr/bin/apt-add-repository", line 88, in <module>
    ppa_info = get_ppa_info_from_lp(user, ppa_name)
  File "/usr/lib/python2.7/dist-packages/softwareproperties/ppa.py", line 83, in get_ppa_info_from_lp
    return json.loads(lp_page)
  File "/usr/lib/python2.7/json/__init__.py", line 326, in loads
    return _default_decoder.decode(s)
  File "/usr/lib/python2.7/json/decoder.py", line 366, in decode
    obj, end = self.raw_decode(s, idx=_w(s, 0).end())
  File "/usr/lib/python2.7/json/decoder.py", line 384, in raw_decode
    raise ValueError("No JSON object could be decoded")
ValueError: No JSON object could be decoded

---

### Post by jawilljr on 2012-03-15
tuX9th made a slight typo... the command should be:

```
sudo apt-add-repository ppa:ubuntu-x-swat/x-updates
```

He forgot the 's' at the end of updates...no biggie.

[Here is the webpage](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

Jerry

---

### Post by AgentZ86 on 2012-03-15
> **jawilljr said:**
> tuX9th made a slight typo... the command should be:

```
sudo apt-add-repository ppa:ubuntu-x-swat/x-updates
```

He forgot the 's' at the end of updates...no biggie.

[Here is the webpage](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

Jerry

Ok cool, thanks

I got it working and yet every indication was that it was still running version 280.13 after reboot etc. 

It was not until I tried the settings / additional hardware and selected to activate the current version again that it installed the 295.20 or I should say activated it

Seems like it should have done this with the apt. process 

Anyhow it's installed and can check to see if the bugs are fixed
Thanks

---

### Post by tuX9th on 2012-03-16
great.
hope it works :)
you should take care that you don't download all the packages in this repo the next time you run the update manager.
put those versions on hold or create an apt config to give this ppa a different rating

[https://wiki.ubuntu.com/Testing/EnableProposed](https://wiki.ubuntu.com/Testing/EnableProposed)

just like that but change the name of "oneric-proposed" to the name of the ppa.

greets

---

