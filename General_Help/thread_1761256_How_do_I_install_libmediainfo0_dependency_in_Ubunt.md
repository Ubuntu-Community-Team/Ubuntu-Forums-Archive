---
title: "How do I install libmediainfo0 dependency in Ubuntu 9.04 x64?"
date: 2011-05-17
forum: General Help
---

### Post by dago1 on 2011-05-17
How do I intall it using the terminal or synaptic for that matter. I need it to install Mediainfo.

---

### Post by papibe on 2011-05-17
Have you tried this ppa version?
```
$ sudo add-apt-repository ppa:shiki/mediainfo
$ sudo apt-get update
$ sudo apt-get install mediainfo
```
Regards.

---

### Post by dago1 on 2011-05-17
I tried those commands and this is what I get:

[IMG]http://i.imgur.com/5Vod9.png[/IMG]

I already have the mediainfo installer sitting in my desktop. It could work by only installing libmediainfo0

---

### Post by papibe on 2011-05-17
to install add-apt-repository:
```
$ sudo apt-get install python-software-properties
```
and then try the commands on my previous post.

I hope it helps.

---

### Post by dago1 on 2011-05-17
I get this:

dago@dago-desktop:~$ sudo apt-get install python-software-properties
[sudo] password for dago: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
python-software-properties is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by papibe on 2011-05-17
I see. I just realized that that way if adding a ppa won't work on 9.x. Try using this [graphical ]("https://help.ubuntu.com/community/Repositories/Ubuntu#Adding PPAs")steps, to add the ppa. Then do the update and the install.

I hope it works this time.

---

### Post by dago1 on 2011-05-18
When trying to manually add the ppa I got this error:

[IMG]http://i.imgur.com/aRPRL.png[/IMG]


This is the full text of the error:

GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 61260473F9D8BC54Failed to fetch cdrom://Ubuntu 9.04 _Jaunty  Jackalope_ - Release Candidate amd64 (20090414.2)/dists/jaunty/main/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom://Ubuntu 9.04 _Jaunty  Jackalope_ - Release Candidate amd64 (20090414.2)/dists/jaunty/restricted/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by papibe on 2011-05-18
Sorry if I haven't been much help, but I have forgotten how things were done on previous releases. In the [mediainfo ppa page]("https://launchpad.net/~shiki/+archive/mediainfo") there's instructions on how to add a ppa to 9.10 (or older). Here they are:

-----------------------------------------------------------------------
**[SIZE="2"]On older (pre 9.10) Ubuntu systems[/SIZE]**

**Step 1:** Visit the PPA's overview page in Launchpad. Look for the heading that reads Adding this PPA to your system and click the Technical details about this PPA link.

**Step 2:** Use the Display sources.list entries drop-down box to select the version of Ubuntu you're using.

**Step 3:** You'll see that the text-box directly below reads something like this:

```
deb http://ppa.launchpad.net/shiki/mediainfo/ubuntu lucid main 
deb-src http://ppa.launchpad.net/shiki/mediainfo/ubuntu lucid main 
```

Copy those lines.

**Step 4:** Open a terminal and type:

sudo gedit /etc/apt/sources.list

This will open a text editor containing the list of archives that your system is currently using. Scroll to the bottom of the file and paste the lines you copied in the step above.

Save the file and exit the text editor.

**Step 5:** Back on the PPA's overview page, look for the Signing key heading. You'll see something like:

```
1024R/F9D8BC54 (What is this?)
``` 

Copy the portion after the slash but not including the help link; e.g. just F9D8BC54.

**Step 6:** Now you need to add that key to your system so Ubuntu can verify the packages from the PPA. In your terminal, enter:

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys F9D8BC54
```

This will now pull down the PPA's key and add it to your system.

**Step 7:** Now, as a one-off, you should tell your system to pull down the latest list of software from each archive it knows about, including the PPA you just added:

```
sudo apt-get update
```

Now you're ready to start installing software from the PPA!

Read more about Personal Package Archives in our help wiki.
-----------------------------------------------------------------------

The installation now should be:
```
$ sudo apt-get install mediainfo
```

Regards.

---

