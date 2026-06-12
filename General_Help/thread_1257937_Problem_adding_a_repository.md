---
title: "Problem adding a repository"
date: 2009-09-04
forum: General Help
---

### Post by KunoNoOni on 2009-09-04
I'm using Ubuntu version 9.04

I was told to add this to the repository so that I could get the latest versions of Battle of Wesnoth but its not working.

***deb [http://download.tuxfamily.org/itwesnoth/debian/](http://download.tuxfamily.org/itwesnoth/debian/) binary/ #wesnoth binary stable/unstable***

When I add that line nothing changes... so I take out the space after debian and Synaptic crashes :)

Then I did some checking and found out why it was crashing and changed the line to:

***deb [http://download.tuxfamily.org/itwesnoth/debian/binary/](http://download.tuxfamily.org/itwesnoth/debian/binary/) wesnoth binary stable/unstable***

Synaptic doesn't crash but it tells me:

[B][I]Failed to fetch http:// download.tuxfamily.org/itwesnoth/debian/binary/dists/wesnoth/binary/binary-i386/Packages 404 Not Found
Failed to fetch http:// download.tuxfamily.org/itwesnoth/debian/binary/dists/wesnoth/stable/unstable/binary-i386/Packages 404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.[/I][/B]

Um... the url to the binaries is just ***[http://download.tuxfamily.org/itwesnoth/binary/](http://download.tuxfamily.org/itwesnoth/binary/)*** the rest of that ***/dists/wesnoth/binary/binary-i386/Packages*** does not exist

So I tried changing things up. I'd edit the repository and change the URI to ***[http://download.tuxfamily.org/itwesnoth/](http://download.tuxfamily.org/itwesnoth/)*** distribution to ***debian*** and components to ***binary stable unstable*** or to just ***binary***

No matter what I do I can't get it to see the latest developmental version of the game. 

:confused:

-KunoNoOni

---

### Post by wiremoons on 2009-09-04
Have you tried to followed the instructions here: 

[http://itwesnoth.valdan.net/en/repository-debian-per-wesnothdebians-repository-for-wesnoth/](http://itwesnoth.valdan.net/en/repository-debian-per-wesnothdebians-repository-for-wesnoth/)

It looks very similar to what you have tried mind :)

I would remove the lines you have added, and replace them with the ones from the above page.  The command would be entered in a Terminal window as follows:

1) Enter: **sudo gedit /etc/apt/sources.list**
2) **Add the following lines to the bottom of the file** (cut and paste is safest way!)  *NB The lines starting with '#' are just comments only.*

# wesnoth binary stable/unstable
deb [http://download.tuxfamily.org/itwesnoth/debian/](http://download.tuxfamily.org/itwesnoth/debian/) binary/
# wesnoth sources stable/unstable
deb-src [http://download.tuxfamily.org/itwesnoth/debian/](http://download.tuxfamily.org/itwesnoth/debian/) sources/ 

3) **Save the file** with the above lines added
4) Enter the command: **sudo apt-get update** in the Terminal window, which should pull down the package information needed from these two Wesnoth repositories

You should see the output in the Terminal windows confirming the downloads?

---

