---
title: "Computer Janitor"
date: 2009-11-08
forum: General Help
---

### Post by mattsegstro on 2009-11-08
The Computer Janitor program under System-Administration was one thing I really noticed and thought was a great addition to Ubuntu 9.10.  I had often wished that Linux would have an easy way of cleaning up stuff, junk that wasn't needed anymore and was just hogging disk space etc.  But when I ran it today it gave me a list of a few dozen items that it thought I should clean (under the "unused" column).  I thought that was great and clicked the button to get rid of them ("do selected tasks") but it gave me a warning telling me that I should be careful "You have chosen to remove 20 software packages. Removing packages that are still needed can cause errors."

What should I do about such a warning?  I figure that if they're under the "unused" column that I can safely get rid of them but I thought I should ask around here before doing anything.  I just closed Janitor and so nothing is gone yet, could someone let me know how safe it is to clean those things, and how important it is to be cleaning out things like that?  If it's safe to do then I might as well, but if it's not safe and not very important then I'll just leave it alone.

Thanks!

---

### Post by tommynz1975 on 2009-11-08
:lolflag: the way your post is worded reminds me of the windows similar program that tells me none of my software has ever been used and should be deleted.

---

### Post by whoop on 2009-11-08
I think that is just a default "be careful" message. The janitor used to list items that I had installed outside of the repository (but it doesn't seem to do that for me any more).

It should be safe to remove the items. But I understand your concern as there are allot of them.

Either post the items in this thread, so we can see if it tries to remove any current 9.10 repository items (which it off course shouldn't) or remove them in fases (and check between fases if everything is working properly, as there is not really a rush to clean it all at once).

---

### Post by winotree on 2009-11-08
What **whoop** said.  That application has really changed!  I just downloaded it [again] and it appears to be completely different -- will keep it for a few months to see what it suggests.

---

### Post by mattsegstro on 2009-11-08
Thanks for the suggestions, so here are the things it tells me to remove:

adobe-flashplugin
adobereader-enu
avast4workstation
clamav (by the way, for these ones I'm pretty sure I can get rid of them, I installed ClamAV from the "Ubuntu Software Center" and didn't like the way it worked so I removed it and put Avast on, just thought I would confirm for even these!)
clamav-base
clamav-freshclam
libbit-vector-perl
libcarp-clan-perl
libclamav6
libconfig-tiny-perl
libdate-calc-perl
libdigest-hmac-perl
libdigest-sha1-perl
libfile-find-rule-perl
libnet-dns-perl
libnet-ip-perl
libnumber-compare-perl
libtext-glob-perl
libtommath0
realplay

Thanks again!

---

### Post by scouser73 on 2009-11-08
I edit the menus when I ever do a fresh install of Ubuntu and Computer Janitor is the first thing to be hidden from my view.  I've mistakenly thought that it was there to help and not to be a hindrance.

---

### Post by Bonster on 2009-11-08
Computer Janitor is crap, Use bleachbit

---

### Post by mattsegstro on 2009-11-08
lol to what scouser73 said, maybe it's not worth my while to use, but what is this bleachbit program?

---

### Post by Brian Vaughan on 2009-11-08
> **mattsegstro said:**
> 
clamav (by the way, for these ones I'm pretty sure I can get rid of them, I installed ClamAV from the "Ubuntu Software Center" and didn't like the way it worked so I removed it and put Avast on, just thought I would confirm for even these!)

I'd bet that if you looked in Synaptic, you'd find those packages listed under "auto removable," which is a list of packages that were installed as dependencies to some other package, which you've removed. In that case, they really aren't in use, and you can safely remove them.

By the way, ClamAV is really only for checking files in transit to Windows boxes. There really aren't any Linux viruses -- Unix and Linux carefully control what code is authorized to execute. [See this section of the Wikipedia article on Computer viruses.]("http://en.wikipedia.org/wiki/Computer_virus#The_vulnerability_of_operating_systems_to_viruses") (There are other security hazards, but not viruses.)

---

### Post by mattsegstro on 2009-11-08
Where would I find "auto removable"?  I looked in Synaptic and I can't find it, maybe I'm just stupid!

And I know there aren't really any Linux virus', but I have lots of contact with Windows computers via email, flash drives and networks and so I want to try and keep those machines safe.  Also, coming from Windows, I just have this idea that I should at least take some precautions, I know it's stupid but for a Windows user, it just becomes so deeply ingrained in you to protect your machines that it's tough to sit back and relax and ignore stuff like that!

---

### Post by winotree on 2009-11-09
> **mattsegstro said:**
> Where would I find "auto removable"?  I looked in Synaptic and I can't find it, maybe I'm just stupid!

And I know there aren't really any Linux virus', but I have lots of contact with Windows computers via email, flash drives and networks and so I want to try and keep those machines safe.  Also, coming from Windows, I just have this idea that I should at least take some precautions, I know it's stupid but for a Windows user, it just becomes so deeply ingrained in you to protect your machines that it's tough to sit back and relax and ignore stuff like that!
On lower-left side of Synaptic, there's Sections, Status, Origins, etc.  Click Status.  Those relevant files should show in upper-left side along with Installed, Not Installed, etc.  You can click them to delete them.  Hope you'll find that Synaptic seems rather user-friendly.

On another note -- Bleachbit has matured in the several months since I last saw it.  And I didn't have to wait to use it, either.  ;)

---

### Post by mattsegstro on 2009-11-09
Thanks for the instructions... so just to confirm (I'm really worried about doing something to my system like this! lol) I click on Status, then go down to the 3rd level "Installed (auto removable)" and any package in that list can be safely removed?

Thanks again, and I may give that bleachbit program a shot, thanks for that recommendation!

---

### Post by winotree on 2009-11-09
> **mattsegstro said:**
> Thanks for the instructions... so just to confirm (I'm really worried about doing something to my system like this! lol) I click on Status, then go down to the 3rd level "Installed (auto removable)" and any package in that list can be safely removed?

Thanks again, and I may give that bleachbit program a shot, thanks for that recommendation!
Technically, yes.  It appears that you had deleted a program and these are residual packages -- didn't someone already mention this?  :|  If, or when in doubt, Google the package names, then determine whether or not you still need them or get on-line and ask, like now.  To be fair, Synaptic Package Manager has never done me wrong in two years over several distributions.  ;)

---

### Post by mattsegstro on 2009-11-09
Alright, I am just on my way out the door right now so I can't really try it now but when I get home I will give Synaptic a shot, let it remove all those programs (btw, should I use removal or complete removal?) and I'll just assume it knows what it's doing.

Thanks for putting up with these questions, I realize that no one can tell me anything for sure without actually being here and looking at my computer and what's on it, and even then maybe you can't be sure.  I'll just try it and see what happens, I just want to know about that removal or complete removal and then I'll quit asking stupid questions :D

Thanks again for your patience.

---

### Post by winotree on 2009-11-09
> **mattsegstro said:**
> Alright, I am just on my way out the door right now so I can't really try it now but when I get home I will give Synaptic a shot, let it remove all those programs (btw, should I use removal or complete removal?) and I'll just assume it knows what it's doing.

Thanks for putting up with these questions, I realize that no one can tell me anything for sure without actually being here and looking at my computer and what's on it, and even then maybe you can't be sure.  I'll just try it and see what happens, I just want to know about that removal or complete removal and then I'll quit asking stupid questions :D

Thanks again for your patience.
The removal leaves configuration files behind to ease a re-installation if my memory serves.  The other is self-explanatory -- I always use it.  I mean you can still install or re-install something...

---

### Post by winotree on 2009-11-09
As an afterthought why don't you copy+paste those files-packages somewhere safe so that if this doesn't go the way you expect you'll still have a means to restore your system.

---

### Post by mattsegstro on 2009-11-09
Well I installed and ran BleachBit (as root, that might have been a dumb idea but I figured that if I'm cleaning up, I might as well see what wrecks my system and what doesn't!), and so I didn't even bother backing up the packages because my system is still relatively new and doesn't have things like music and movies on it and everything, so it wouldn't take me all that long to do a fresh install if I screwed something up.  9.10 is still fairly new so I don't have all that much on here to lose!

Thanks again, I'll come back if I have problems but I think that things are running just fine, the way they're supposed to be, after BleachBit and Synaptic

---

### Post by mattsegstro on 2009-11-10
Let me start off by saying that I don't blame any of you for what happened!  My last post was premature.  I posted before running all of those things, I just wanted to post, knowing that I would have to go through the entire process of logging into things again like the forums, and I honestly thought that the things I was doing would be safe enough that I wouldn't run into any problems.  I thought I would post, run those things, and then deal with everything else in the morning, it's nearing midnight here and about time for me to head off to bed.

However, something came up and I needed to send some emails after running all those things like Synaptic and Bleachbit, and was dismayed when my contacts were gone.  Either Bleachbit or Synaptic deleted all my contacts in Evolution.  I'm not exactly sure what else it has done as I haven't really had a chance to do much else, but surprisingly, when I tried to log back into the forums, it had my password saved still.  It didn't automatically keep me logged in so it did remove something, but yet it kept the information behind in Firefox.  In Bleachbit I selected everything so that it would remove as much as possible (but either I'm stupid or it didn't ask me about Evolution contacts!).  So it just baffles me as to why this program would remove something as obviously useful as my contacts list, which it has absolutely no reason to clean out, and yet keep my saved passwords in Firefox.

Again let me say that I'm not posting to get mad at any of you for the suggestions you made, I'm simply posting this so that maybe someone looking around here will not make the same mistake I made and will leave these things alone in the future.  Bleachbit is not worth running.  Ever.  Obviously, as other posters have said, neither is Computer Janitor, and while I'm pretty sure that the cleaning Synpatic did wasn't to blame for my problems, that's probably best left alone as well.  I'm not sure why a program would be created to do such stupid tasks, but it is certainly not worth anyone's time to run or bandwidth to download.

Sorry if I'm ranting here, I have just been on "cloud 9" ever since starting to run 9.10 the day it came out.  I loved every minute of it, I thought it was the greatest thing ever and now I'm faced with this.  This is not a big enough issue for me to stop using Ubuntu but I really am disappointed that these things can happen and that no warnings are given.  Running Bleachbit it warned me that a certain option would remove all my bookmarks (I don't have any so it didn't bother me), but why couldn't such a warning have been given that "selecting this will remove all your contacts" or something like that?  While it's not a big issue for someone like me with just about nothing to lose in testing these kinds of programs out on my system (I haven't lost anything at all in fact other than time), for someone who has a lot to lose this could turn them off from Linux altogether.  Or for someone who is simply trying Linux out of curiosity rather than a deep rooted hatred for Windows like I have, this could cause them to go back to Windows.  The reason why I'm sticking with Ubuntu is because I'm waiting for Mint to release a new version this month, and for Mepis and PCLinuxOS to release versions with the updated KDE4 in the future for me to try out, and I'm desperate to not need to go back to Windows.  But for someone else, this could turn them off altogether and Linux doesn't need that right now.

People, learn to write programs that do what we want them to do and don't do what we don't want them to do.  For example, for the Windows users out there, I used to always run CCleaner.  I never once used it's built in backup function for registry edits and always ignored it's warnings about cleaning because it did what I asked it to and nothing more.  Bleachbit didn't do what I asked it to do, and instead did what I didn't ask it to.  Please write better programs!

OK my rant is done, sorry for this being so long, I'm just really frustrated now.

---

### Post by pataphysicianu on 2009-11-10
I thought I would post this in this thread as well. Just in case anyone has  a similar problem.

Were your contacts in evolution actually local, or do you have a link to online google contacts, or exchange server contacts?

Online evolution contacts like google's or exchange are just put into the cache, if the cache is wiped out, it just gets them from the online service again, but only if your online and logged in. Bleachbit will delete this file, but it is no big deal as all these contacts are actually online somewhere. there is a setting when you set up google or exchange contacts to also copy them to you local contact repository, these files are untouched by Bleachbit.

My guess is you set up online contacts and then Bleachbit cleared the cache, then you opened up evolution when you were not online, so evolution couldn't grab the contacts from online, and so showed nothing.

---

