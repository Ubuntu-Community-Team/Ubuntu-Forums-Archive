---
title: "Can't open Software Center, Update manager, or Synaptic"
date: 2010-12-01
forum: General Help
---

### Post by Jean13 on 2010-12-01
Hi, green user here

I can't open neither Ubuntu Software Center, the Update Manager or the Synaptic Package Manager. 

When I try to open the Software Center, I get "Starting Ubuntu Software Center" then it stops and I have nothing

When I try to open the Update Manager, it says it's "reading package list" then I get this error:


'E:Encountered a section with no Package: header, E: Problem with MergeList /var/lib/apt/lists/packages.medibuntu.org_dists_maverick_free_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

Note : I added a space in E: Problem to avoid getting an emote

When I try to open Synaptic package manager, I get a similar error that says basically the same thing with more details:

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/packages.medibuntu.org_dists_maverick_free_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

What do?

---

### Post by sikander3786 on 2010-12-01
Remove your list files by,

```
sudo rm /var/lib/apt/lists/* -vf
```

And run apt-get update,

```
sudo apt-get update
```

Don't worry, those files will be recreated when you run apt-get update.

---

### Post by Jean13 on 2010-12-01
Thanks, it worked wonder!

---

### Post by sikander3786 on 2010-12-01
> **Jean13 said:**
> Thanks, it worked wonder!
Nice to hear that :-)

You can now mark this thread Solved using [COLOR="Red"]**Thread Tools**[/COLOR] near the top of this page.

Happy Ubuntu-ing!

---

### Post by Lamukra on 2011-02-14
Did not work for me! :(

Saying Starting [app name] and that is it... problem started after playing with plymouth splash screen manager "Zorin Splash Screen Manager"

Any advice?

---

### Post by Lamukra on 2011-02-14
Sorry... found a solution in this thread [http://ubuntuforums.org/showthread.php?t=1394618](http://ubuntuforums.org/showthread.php?t=1394618)

Problem was that when running ```
sudo apt-get update
```
I was getting this

```
Segmentation faultsts... 0%
```


Used this code


```

sudo rm -vf /var/cache/apt/*.bin
sudo aptitude update
sudo aptitude full-upgrade

```
and then
```
sudo apt-get update
```
And since then everything is working
But can you tell me what could be possible broken?

---

### Post by ashgoodman on 2011-03-25
None of the listed solutions work for me.

I haven't installed any new software all I have done is upgrade software already installed and now I am left with a  box that won't update or upgrade.

This is my main work machine so I am basically screwed as i'll have to do a full reinstall and all that entails and I just don't have that kind of time.

I moved away from Windows in order to get away from having to do full reinstalls so I am now feeling pretty frustrated.

Can anyone please suggest a workable solution?

---

### Post by sikander3786 on 2011-03-26
> **ashgoodman said:**
> None of the listed solutions work for me.

I haven't installed any new software all I have done is upgrade software already installed and now I am left with a  box that won't update or upgrade.

This is my main work machine so I am basically screwed as i'll have to do a full reinstall and all that entails and I just don't have that kind of time.

I moved away from Windows in order to get away from having to do full reinstalls so I am now feeling pretty frustrated.

Can anyone please suggest a workable solution?
We need to see the complete outputs of these commands first, please.

```
sudo apt-get install -f
```

```
sudo dpkg --configure -a
```

```
sudo apt-get update
```

---

### Post by ashgoodman on 2011-03-26
HI,

It just says Segmentation faultsts 0%

---

### Post by maverick_ar380m on 2011-05-05
I am encountering right now the same problem and the given solution is not working...please help me...thanks!

---

### Post by newbymick on 2011-06-10
sikander3786 - well done.  Worked for me

---

### Post by iamnotloggedon on 2011-06-30
Having the same problem but a slightly different file path for the error:

```
Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_i18n_Translation-en, E:The package lists or status file could not be parsed or opened.'
```
This example is from Update manager and I've tried ever solution listed above. My terminal doesn't recognize Aptitude as a command and every time I try the other solutions I get an error when I run sudo apt-get update

```
Ign http://us.archive.ubuntu.com natty-updates/universe Translation-en
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.

```Also this is off topic but I noticed this issue in my frantic search for an answer to this question so...: can anybody point me in the right direction to find a thread of how to create an installable program from a C++ file in Code::Blocks that will run on OTHER computers? What I have works on my own machine just fine.

---

