---
title: "Update Manager"
date: 2011-05-19
forum: General Help
---

### Post by northwestern on 2011-05-19
Whenever I load the update manager and press the "check" button I get the following message after the cache has updated.[B]
Failed to download repository information

Check your internet connection[/B]

My internet connection is working fine (UK)
The message in the details section reads:-

W:Failed to fetch [http://ppa.launchpad.net/sikon/steadyflow+/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/sikon/steadyflow+/ubuntu/dists/natty/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/sikon/steadyflow+/ubuntu/dists/natty/main/binary-i386/Packages](http://ppa.launchpad.net/sikon/steadyflow+/ubuntu/dists/natty/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

Any help in solving this problem would be appreciated.
Regards
Northwestern

---

### Post by pakidevil on 2011-05-19
open up a terminal and type this command .. hopefully, it should work ..

sudo apt-get update

---

### Post by Plueonic on 2011-05-19
It seems you somehow have an extra + sign..what does the repository line look like? You can see it from synaptic>settings>repositories>3rd party... or *cat /etc/apt/sources.list.d/sikon-steadyflow**

---

### Post by northwestern on 2011-05-19
Suggestion number 1 **sudo apt-get update **did seemed not to make any difference.

The following lines appeared in terminal when entering the required command


deb [http://ppa.launchpad.net/sikon/steadyflow+/ubuntu](http://ppa.launchpad.net/sikon/steadyflow+/ubuntu) natty main
deb-src [http://ppa.launchpad.net/sikon/steadyflow+/ubuntu](http://ppa.launchpad.net/sikon/steadyflow+/ubuntu) natty main
deb [http://ppa.launchpad.net/sikon/steadyflow/ubuntu](http://ppa.launchpad.net/sikon/steadyflow/ubuntu) natty main
deb-src [http://ppa.launchpad.net/sikon/steadyflow/ubuntu](http://ppa.launchpad.net/sikon/steadyflow/ubuntu) natty main
deb [http://ppa.launchpad.net/sikon/steadyflow+/ubuntu](http://ppa.launchpad.net/sikon/steadyflow+/ubuntu) natty main
deb-src [http://ppa.launchpad.net/sikon/steadyflow+/ubuntu](http://ppa.launchpad.net/sikon/steadyflow+/ubuntu) natty main
deb [http://ppa.launchpad.net/sikon/steadyflow/ubuntu](http://ppa.launchpad.net/sikon/steadyflow/ubuntu) natty main
deb-src [http://ppa.launchpad.net/sikon/steadyflow/ubuntu](http://ppa.launchpad.net/sikon/steadyflow/ubuntu) natty main
Regards
Northwestern

---

### Post by hwttdz on 2011-05-19
You can delete all but the last two lines there and you should be good to go.

---

### Post by northwestern on 2011-05-19
How do I delete the lines ?

Regards
Northwestern

---

### Post by Plueonic on 2011-05-19
> **northwestern said:**
> How do I delete the lines ?

Regards
Northwestern
```
gksu gedit /etc/apt/sources.list.d/sikon-steadyflow-natty.list
```If there is a seperate file called  'sikon-steadyflow**+**-natty.list'
```
sudo rm /etc/apt/sources.list.d/sikon-steadyflow**+**-natty.list
```After saving the file, run *sudo apt-get update* to refresh the software index.

//(It would be easier to use the repository dialog in synaptic)

---

### Post by northwestern on 2011-05-19
Thanks for your reply.
I am new to ubuntu and not sure what you meant, when I entered your suggestion in the terminal GEDIT opened with the following lines 
deb [http://ppa.launchpad.net/sikon/steadyflow/ubuntu](http://ppa.launchpad.net/sikon/steadyflow/ubuntu) natty main
deb-src [http://ppa.launchpad.net/sikon/steadyflow/ubuntu](http://ppa.launchpad.net/sikon/steadyflow/ubuntu) natty main
From then on I am at a loss what to do.

Regards
Northwestern

---

### Post by Plueonic on 2011-05-19
As I said earlier, it would be a lot easier to just disable the sources with the + sign from synaptic..but if you really want to do this manually, post the contents of the directoy /etc/apt/sources.list.d/

---

### Post by northwestern on 2011-05-19
How do I disable them in synaptic.

Regards

---

### Post by Plueonic on 2011-05-19
Open Synaptic > settings menu > repositories > other software tab and you'll see something similar to this :  (image from [ubuntu wiki]("https://help.ubuntu.com/community/Repositories/Ubuntu#Removing%20&%20Disabling%20Repositories"))

[IMG]https://help.ubuntu.com/community/Repositories/Ubuntu?action=AttachFile&do=get&target=SoftwareSources-OtherSoftware.png[/IMG]

Untick/remove the source which is causing trouble

---

### Post by Frogs Hair on 2011-05-19
Synaptic > Settings > Repository > Other Software From there you can remove them from the list .

---

### Post by ste_bran on 2011-05-20
I am running 10.10, and getting the same error as OP. Also a noob, like OP. :)

Following the instructions in this thread as I understand them, I went to System at the top of my screen, then Administration>Synaptic Package Manager>settings>repositories, then clicked the "Other Software" tab and got a similar-looking screen to the one in Plueonic's post. However, none of the entries shown agrees with the problematic entries in my error message, which are [http://archive.ubuntu.com/ubuntu/dists/maverick/release.gpg](http://archive.ubuntu.com/ubuntu/dists/maverick/release.gpg) and [http://archive.canonical.com/ubuntu/dists/maverick/release.gpg](http://archive.canonical.com/ubuntu/dists/maverick/release.gpg)

Maybe I am in the wrong place, but the only place I know where it says "Synaptic" is in the System>administration menu.

My other question is once I do find the offending files and untick them as suggested by Plueonic, how do I know I am not removing a repository that I need?

Related problem? When I try to upgrade to Natty, I get message about not able to find [http://extras.ubuntu.com/ubuntu/dists/natty/Release.gpg](http://extras.ubuntu.com/ubuntu/dists/natty/Release.gpg)     and not able to find some indexes, then it doesn't upgrade.

---

