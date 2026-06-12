---
title: "failed to fetch Firefox ppa"
date: 2012-09-27
forum: General Help
---

### Post by eival on 2012-09-27
Failed to fetch [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

its said this for the past few days, every other updates have been fine

---

### Post by Cavsfan on 2012-09-27
Delete that repository as it is no longer there.
You can get firefox 15.0.1, which is what I have from [[COLOR=blue]_here_[/COLOR]]("http://www.liberiangeek.net/2012/04/download-and-install-firefox-manually-in-ubuntu-12-04-precise-pangolin/").

Just change the commands to match the file you download.

Hope this helps. :)

---

### Post by Cavsfan on 2012-09-27
You might need to download it from here: [[color=blue]_http://www.mozilla.org/en-US/firefox/all.html_[/COLOR]](http://www.mozilla.org/en-US/firefox/all.html)

But, once downloaded, the instructions on that previous page should work.

---

### Post by Cavsfan on 2012-09-27
I think I jumped the gun. I was in Precise when I posted the above.
Now I am in Lucid and am getting this exact same error.
I am getting this on 2 ppas.

```
Err http://ppa.launchpad.net lucid/main Packages                                                      
  404  Not Found
W: Failed to fetch http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/lucid/main/binary-amd64/Packages.gz  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
```Which means everyone on Lucid should be getting this error.
Hopefully someone has an answer.

---

### Post by eival on 2012-09-27
> **Cavsfan said:**
> I think I jumped the gun. I was in Precise when I posted the above.
Now I am in Lucid and am getting this exact same error.
I am getting this on 2 ppas.

```
Err http://ppa.launchpad.net lucid/main Packages                                                      
  404  Not Found
W: Failed to fetch http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/lucid/main/binary-amd64/Packages.gz  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
```Which means everyone on Lucid should be getting this error.
Hopefully someone has an answer.


yeah im on Lucid too, glad to see its not just me getting the error tho.

---

### Post by dcstar on 2012-09-28
> **eival said:**
> yeah im on Lucid too, glad to see its not just me getting the error tho.

Then you have had your question answered, please mark the thread now.

---

### Post by Cavsfan on 2012-09-28
> **dcstar said:**
> Then you have had your question answered, please mark the thread now.

**David**, I still have the same problem and I believe so does **eival** so the thread is not solved.

Hopefully, someone has an idea of what the problem is. I have not been spending a lot of time on Lucid.
But, I am continuing to get these 2 errors from 2 ppas.

---

### Post by wheeze on 2012-09-28
Here's your problem, there are no distributions listed under the firefox-stable branch of that PPA.

---

### Post by Cavsfan on 2012-09-28
> **wheeze said:**
> Here's your problem, there are no distributions listed under the firefox-stable branch of that PPA.

Thanks for that. I guess they stopped supporting Mozilla Firefox stable updates.
The Ubuntu versions were deleted on September 25, 2012
I did see that this exists: ```
http://ppa.launchpad.net/mozillateam/firefox-next/ubuntu/dists/lucid/
```It says:
"This PPA will contain Milestone builds of the next version of Firefox (alpha, beta, RC)". This is for precise, oneiric, natty, maverick and lucid.

Here is the page with the instructions on adding it:
[[COLOR=blue]_http://www.ubuntuupdates.org/ppa/mozilla_team_firefox_next?dist=lucid_[/COLOR]]("http://www.ubuntuupdates.org/ppa/mozilla_team_firefox_next?dist=lucid")


When I added that ppa and entered **sudo apt-get update** and **sudo apt-get upgrade**, the other error went away and I am being offered Firefox version 16!
Pretty sweet. :)
This should be the answer to your problem **eival**.
I had to delete the firefox-stable ppa from **/etc/apt/sources.list.d/**.

---

### Post by eival on 2012-09-28
> **Cavsfan said:**
> Thanks for that. I guess they stopped supporting Mozilla Firefox stable updates.
The Ubuntu versions were deleted on September 25, 2012
I did see that this exists: ```
http://ppa.launchpad.net/mozillateam/firefox-next/ubuntu/dists/lucid/
```It says:
"This PPA will contain Milestone builds of the next version of Firefox (alpha, beta, RC)". This is for precise, oneiric, natty, maverick and lucid.

Here is the page with the instructions on adding it:
[[COLOR=blue]_http://www.ubuntuupdates.org/ppa/mozilla_team_firefox_next?dist=lucid_[/COLOR]]("http://www.ubuntuupdates.org/ppa/mozilla_team_firefox_next?dist=lucid")


When I added that ppa and entered **sudo apt-get update** and **sudo apt-get upgrade**, the other error went away and I am being offered Firefox version 16!
Pretty sweet. :)
This should be the answer to your problem **eival**.
I had to delete the firefox-stable ppa from **/etc/apt/sources.list.d/**.


so we cant get stable updates, only beta/prereleases?

am i understanding that correctly?


theres no way to just let Firefox standalone from the repos, and get its own updates from Mozilla?

---

### Post by father_ted on 2012-09-28
This is the PPA for the aurora firefox builds. 

[http://ppa.launchpad.net/ubuntu-mozilla-daily/firefox-aurora/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/firefox-aurora/ubuntu)

I am currently having difficulty with it though. but only since the 21-9-2012

---

### Post by Cavsfan on 2012-09-28
> **Cavsfan said:**
> Thanks for that. I guess they stopped supporting Mozilla Firefox stable updates.
The Ubuntu versions were deleted on September 25, 2012
I did see that this exists: ```
http://ppa.launchpad.net/mozillateam/firefox-next/ubuntu/dists/lucid/
```It says:
"This PPA will contain Milestone builds of the next version of Firefox (alpha, beta, RC)". This is for precise, oneiric, natty, maverick and lucid.

Here is the page with the instructions on adding it:
[[COLOR=blue]_http://www.ubuntuupdates.org/ppa/mozilla_team_firefox_next?dist=lucid_[/COLOR]]("http://www.ubuntuupdates.org/ppa/mozilla_team_firefox_next?dist=lucid") 


When I added that ppa and entered **sudo apt-get update** and **sudo apt-get upgrade**, the other error went away and I am being offered Firefox version 16!
Pretty sweet. :)
This should be the answer to your problem **eival**.
I had to delete the firefox-stable ppa from **/etc/apt/sources.list.d/**.

> **eival said:**
> so we cant get stable updates, only beta/prereleases?

am i understanding that correctly?


theres no way to just let Firefox standalone from the repos, and get its own updates from Mozilla?

From what all I have seen this seems to be true. No Ubuntu version is listed in that ppa.
The only other option is to remove the ppa and download the stable version from Mozilla.
[[COLOR=blue]_http://www.mozilla.org/en-US/firefox/fx/#desktop_[/COLOR]]("http://www.mozilla.org/en-US/firefox/fx/#desktop") This is version 15.0.1 the most recent stable version.

I am using version 16 right now and until I have a problem with it. I will use that stable ppa.
The first time I have a problem I will do as I mentioned above.

Unless someone knows more about where the stable firefox ppa went to.

---

### Post by Cavsfan on 2012-09-28
As you can see from this site in the warning in red:

[[COLOR=blue]_http://www.ubuntuupdates.org/ppa/mozilla_team_firefox_stable_[/COLOR]]("http://www.ubuntuupdates.org/ppa/mozilla_team_firefox_stable")

Check out this thread by **lovinglinux** [[COLOR=blue]_Firefox +1 Mega Thread _[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1712247")

**lovinglinux** is a Firefox addon developer among other things.

---

### Post by pqwoerituytrueiwoq on 2012-09-28
[FONT=Courier New]15.0.1+build1-0ubuntu0.10.04.1[/FONT] is available in the default repos last i checked 
[FONT=Courier New]sudo apt-get install firefox[/FONT]

---

### Post by Cavsfan on 2012-09-28
> **pqwoerituytrueiwoq said:**
> [FONT=Courier New]15.0.1+build1-0ubuntu0.10.04.1[/FONT] is available in the default repos last i checked 
[FONT=Courier New]sudo apt-get install firefox[/FONT]

The only problem is that we installed this: [FONT=Courier New]ppa:mozillateam/firefox-stable[/FONT] many moons ago.

And if you look at [[COLOR=blue]_this_[/COLOR]]("http://www.ubuntuupdates.org/ppa/mozilla_team_firefox_stable") you'll see this:
[COLOR="Red"] WARNING: all packages have been deleted from this repository [/COLOR]

---

### Post by eival on 2012-09-28
could this be because the 10.4 LTS cycle is coming to an end?

this might be what finally forces me to upgrade to the 12 LTS

---

### Post by Cavsfan on 2012-09-28
How right you were **pqwoerituytrueiwoq**!
Nice name BTW.

All you have to do **eival** is:
Enter this in terminal to get rid of that ppa:
**sudo ppa-purge ppa:mozillateam/firefox-stable**
Then answer "Y" to all of the prompts.

I made a backup of my bookmarks in a json file but, then didn't need it. 
It's probably better to do that though.
Then I purged firefox and whatever it took with it.
**sudo apt-get purge firefox**
Then **sudo apt-get update && sudo apt-get install firefox** and BAM I had [FONT=Times New Roman]Firefox version 15.0.1 installed[/FONT].

I guess the repositories caught up. I know you needed that ppa to obtain updates at one time.
I haven't been in Lucid that much and didn't notice until now.
But, the later versions of Ubuntu have the most up to date version of firefox in their repositories.

---

### Post by Cavsfan on 2012-09-28
> **eival said:**
> could this be because the 10.4 LTS cycle is coming to an end?

this might be what finally forces me to upgrade to the 12 LTS

No, see my previous post. The repositories were finally updated so that the most up to date version of Firefox is there now. :)

I'm waiting until pretty close to April 2013 to get rid of Lucid. I believe it is the best Ubuntu I have used.

---

### Post by eival on 2012-09-28
okay i removed the PPA, but do i have to re-add one to continue getting updates for the stable 15.1+ when i check for updates using Update Manager or will they still come through?

id rather avoid having to delete and reinstall while securing all my bookmarks/passwords/addons if i can bypass doing that.

---

### Post by Cavsfan on 2012-09-28
> **eival said:**
> okay i removed the PPA, but do i have to re-add one to continue getting updates for the stable 15.1+ when i check for updates using Update Manager or will they still come through?

id rather avoid having to delete and reinstall while securing all my bookmarks/passwords/addons if i can bypass doing that.

Yeah, you are good to go as you are. :)
Both of our problems are resolved.

---

### Post by Cavsfan on 2012-10-02
In case you used Thunderbird and had the Mozilla ppa installed for that.
It was deleted yesterday 10/1/12.
I just deleted that source and everything is fine. :D

---

### Post by Cavsfan on 2012-10-09
Eival, could you mark this thread as solved through thread tools at the top right?
The Firefox and Thunderbird updates are now gotten through the regular repositories.

---

### Post by eival on 2012-10-10
yeah i was just gonna post about the update today, good to know


edit- actually theres no option to edit the OP or the other posts, i guess its been too long. so a mod can change it or lock the thread.

---

### Post by eival on 2012-10-10
> **Cavsfan said:**
> Eival, could you mark this thread as solved through thread tools at the top right?
The Firefox and Thunderbird updates are now gotten through the regular repositories.

nvm, i did it thru Thread Tools, usually just edited in the past.:popcorn:

---

