---
title: "Is There a Repository Downloader Out There?"
date: 2010-06-02
forum: General Help
---

### Post by cbh2000 on 2010-06-02
I was just wondering if there is an application that will run on both Windows and Linux that is capable of downloading packages from Debian (Ubuntu) and openSUSE repositories for offline use.  And I don't mean the *entire* repository, just select packages and their dependencies.

Does anybody know if such a program exists?

If not, then I will make one; but I do not want to duplicate the efforts of another...

---

### Post by chris4585 on 2010-06-03
I think this is what you want. [http://keryxproject.org/]("http://keryxproject.org/")

---

### Post by Ebere on 2010-06-03
> **cbh2000 said:**
> I was just wondering if there is an application that will run on both Windows and Linux that is capable of downloading packages from Debian (Ubuntu) and openSUSE repositories for offline use.  And I don't mean the *entire* repository, just select packages and their dependencies.

Does anybody know if such a program exists?

If not, then I will make one; but I do not want to duplicate the efforts of another...

Here is the solution I worked out.

To choose the packages you want to download...

Open Synaptic.

Choose the packages that you want to download. Do NOT press apply.

Now go to >File, and choose "Generate Package Download Script".

Choose a name for your script, and where to save it.

Copy that file to a USB stick or something similar, to carry with you, to where you will download the packages.

~~~~~~~

To download the packages...

If you are running windows, you will have to take along the linux "LiveCD", and boot from that.

If already running linux, no problemo.

Now, find that script file.

Create a new folder, in the place that you want to save the packages to.

Copy the script file into that folder.

-RIGHT- click on the script, and choose to run it in a terminal window.

The script will run, and will download all the files. 

You'll know when it is finished, because the terminal window will close.

(I found the other options for running the script to be unsatisfactory, because it was impossible to tell when the script was finished running.)

Carry home your new packages.

~~~~~~~~~~

On the home machine, copy the complete folder to your computer. 

The home folder is probably the best place for it, at this time.

Now, open synaptic again.

Go to >File, and choose "Add downloaded packages".

Browse to the folder you have just copied to your home folder, and choose to "open" it.

Synaptic should do the rest.

~~~~~~~~~~~~

On thing that I could wish they would do better is to actually add -EVERYTHING-  to the download script, that you are going to need.

I have done this a couple of times, already.

I thought it was kind of cool that synaptic will not only add the package that you request, to your download list.. But it adds other files/packages that this one would "depend" on.

Only thing is... It doesn't do the job fully.

What happens is that once you get the packages back home, and get to installing them, Synaptic decides it has to download even more packages, to make what you have already downloaded, -work-.

IOW, it seems to be grabbing those files/packages that have a direct dependency need, but it doesn't seem to follow through and grab the files/packages that THOSE files/packages wil need, as well.

---

### Post by Ebere on 2010-06-03
> **chris4585 said:**
> I think this is what you want. [http://keryxproject.org/](http://keryxproject.org/)

That looks pretty good !

I wonder if it will ever be added to the repositories ? (Or has it been, and my synaptic simply isn't finding it ?)

As good as it looks, I'm not really sure I want to be downloading and installing something that is not in the repositories.

---

### Post by oldos2er on 2010-06-03
[http://excid3.com/blog/2010/05/keryx-package-and-ppa/](http://excid3.com/blog/2010/05/keryx-package-and-ppa/)

Keryx' author occasionally posts in the forums, and in my opinion is trustworthy.

---

### Post by philinux on 2010-06-03
Moved to General Help forum.

---

### Post by cbh2000 on 2010-06-03
Wow!  I didn't know that something that polished even existed!  Thanks, Chris!  (It even runs on Windows...  Hmmm...)

However, I am running openSUSE, and my friends run Ubuntu...  With Novell up for sale, the future of openSUSE is uncertain, so I may be hopping to another.  Chakra is looking good!

Anyway, I was hoping that there was one that could use *any* type of repository; be it Debian, SUSE, Arch, et cetera...

@Ebere  Most computers I have access to run Windows.  Booting a LiveCD would be much harder then simply running a program (because of drivers and such).

Today starts the project, PackageRat / PackRat / RepositoryRat / RepoRat (I have not decided on a name yet).

I plan on:
- Using Qt 4.
- A GUI and command line interface (the GUI will simply be a front-end to the command line interface).
- Support of Windows, Linux, OS X, Windows CE/Mobile.
- Support of _all_ repository based operating systems (not just Linux) through user provided configuration files.
- The ability to only download packages needed.

I am thinking about:
- Automatic "single click" installation (on the target machine).
- Offline repository generation (like AptOnCD or YaST's local directory repository importation ability).
- Mirror (the ability to download the entire repository).
- Running as a service, automatically downloading updates, etc., on the internet-enabled computer.
- PackageKit integration.
(None of these would be hard, except for the repository generation idea.)


I am open to suggestions and will open my work to the public in the "Programming" section, hopefully sometime in August.  I will monitor this thread.

Thanks for the help, Ubuntu community!

---

### Post by chris4585 on 2010-06-03
> **oldos2er said:**
> [http://excid3.com/blog/2010/05/keryx-package-and-ppa/](http://excid3.com/blog/2010/05/keryx-package-and-ppa/)

Keryx' author occasionally posts in the forums, and in my opinion is trustworthy.

I second this, I think the developer for this is actually in my LoCo.

---

### Post by EXCiD3 on 2010-06-03
> **Ebere said:**
> That looks pretty good !

I wonder if it will ever be added to the repositories ? (Or has it been, and my synaptic simply isn't finding it ?)

As good as it looks, I'm not really sure I want to be downloading and installing something that is not in the repositories.

It's okay. Since Keryx's goal is to run on flash drives, I had not really considered spending time on building a package for Keryx yet. However, that being said, several people have requested it, and it makes things simpler to just install the deb on your online machine so I've created a PPA on launchpad where you can get the Keryx deb package. I'm working on getting Keryx sponsored and into the official Ubuntu repositories soon! Just use the link posted earlier to my blog ([http://excid3.com](http://excid3.com)) and you can find the PPA listed there. Thanks guys!


> **chris4585 said:**
> I second this, I think the developer for this is actually in my LoCo.
I'm usually in #ubuntu-us-tn and #keryx on irc.freenode.net if you ever need to catch me. :)

---

### Post by Ebere on 2010-06-03
> **EXCiD3 said:**
> It's okay. Since Keryx's goal is to run on flash drives, I had not really considered spending time on building a package for Keryx yet. However, that being said, several people have requested it, and it makes things simpler to just install the deb on your online machine so I've created a PPA on launchpad where you can get the Keryx deb package. I'm working on getting Keryx sponsored and into the official Ubuntu repositories soon! Just use the link posted earlier to my blog ([http://excid3.com](http://excid3.com)) and you can find the PPA listed there. Thanks guys!



I'm usually in #ubuntu-us-tn and #keryx on irc.freenode.net if you ever need to catch me. :)

Ok, well I'm convinced.

:)

I'll give it a try the next time I have major upgrades to do, or want to download a huge lot of packages.

It took me a while to figure out my own way of doing it. (as posted above) And during the searching required to find all the info I needed, I ran across very many others with the same need.

Bottom line, it's a very needed project. I am glad that you have tackled it.

Thank you.

---

### Post by EXCiD3 on 2010-06-03
> **Ebere said:**
> Ok, well I'm convinced.

:)

I'll give it a try the next time I have major upgrades to do, or want to download a huge lot of packages.

It took me a while to figure out my own way of doing it. (as posted above) And during the searching required to find all the info I needed, I ran across very many others with the same need.

Bottom line, it's a very needed project. I am glad that you have tackled it.

Thank you.

Keep in mind that it's still relatively new and dependency calculation (especially for large groups of packages) can miss a few dependencies on occasion. I'm still working on this quite a bit and if you know anyone who would be interested in contributing send them my way. I could certainly use the help.

---

### Post by cbh2000 on 2010-06-04
> **Ebere said:**
> ... I ran across very many others with the same need.

Bottom line, it's a very needed project. ...

I couldn't agree more.  This was a contributing factor motivating my switch from Kubuntu to openSUSE and could have saved me countless hours of frustration.

---

### Post by cbh2000 on 2010-07-15
**Progress Update for PackRat**
As of today, July 15th, here is the progress on PackRat:
[LIST]
[*]I have settled on a format for the repository specification file.  So far, I have confirmed that openSUSE and Ubuntu will work, but, I am skeptical that *every* Linux-based OS will be supportable.  Who knows, I could be wrong!:D
[*]I am about half way done with the repository description parser, which does most of the work in PackRat.  I *might* have a pre-alpha out next week, but I _seriously_ doubt it.
[/LIST]

I have considered joining the Keryx project, but Python is too slow for my taste.  I'm so picky, that if I had not just started learning it, I would write it all in assembly!  I tried PyQt; it works, but I don't have the patience to use a program made with it...

[B][COLOR="DarkGreen"]openSUSE 11.3 is out today!!![/COLOR]
(It's still green, but better than brown!  Get it at [http://software.opensuse.org/113/en]("http://software.opensuse.org/113/en")

That is what I really wanted to say, but I will also say that I have discovered that there are several programs named PackRat already.  Therefore, I have chosen a new name:
Package
Aggregation
and
Collection
of
Kool-Aid
And
General
Energized
Repository
Arm
Tango

(PACKAGERAT... Cool, eh?)

What!?  Stop looking at me like that![/B]

---

