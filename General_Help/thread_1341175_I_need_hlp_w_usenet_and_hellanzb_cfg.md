---
title: "I need hlp w/ usenet and hellanzb cfg"
date: 2009-11-29
forum: General Help
---

### Post by slope on 2009-11-29
I have now stepped into a mine field. Learning and getting to know how to download from usenet proves rather hard. 

Ok, so I have gotten an account with giganews. That part is covered.
I tried to use giganews preffered usenet client, newsbin under wine but keeps hanging and whatever I do newsbin will not run stable. 

I went the Thunderbird route, but finally saw that Thunderbird is not for use like that. Sry all but for me no good.

I got tips about hellanzb, so that is installed and ready. But I guess I still need to get a news reader client to find nzb files for the downloads I am looking for. 

Anyone knows news reader client that will work good for xubuntu?

---

### Post by DeMus on 2009-11-29
> **slope said:**
> I have now stepped into a mine field. Learning and getting to know how to download from usenet proves rather hard. 

Ok, so I have gotten an account with giganews. That part is covered.
I tried to use giganews preffered usenet client, newsbin under wine but keeps hanging and whatever I do newsbin will not run stable. 

I went the Thunderbird route, but finally saw that Thunderbird is not for use like that. Sry all but for me no good.

I got tips about hellanzb, so that is installed and ready. But I guess I still need to get a news reader client to find nzb files for the downloads I am looking for. 

Anyone knows news reader client that will work good for xubuntu?

In hellanzb, did you made settings for a news server? 
Then look at binsearch.com, or newzleech.com and fill in the search term. It will show you no, some or many answers depending on what you are looking for.
Tick the check-box in front of what you want to download and click the button "Make NZB".
A window will pop up asking what you want to do with the nzb file? Choose to start it and connect it to hellanzb: /usr/bin/hellanzb and make it permanent.
That's about it. Have fun.

---

### Post by slope on 2009-11-29
I'll have hellanzb running now. Downloading one file. Really get my money worth of bandwidth. :-))

I have not been able to get SSL working. I had to set SSL = False in cnfg.
I get an error that I don't have SSl installed.

**Edited:**

```
sudo apt-get install python-pyopenssl
```

Did the trick. Now it works fine using SSL.

---

### Post by slope on 2009-11-29
The only thing I now need is a really easy to use **news reader client** so I can find what I need to download. 

Right now I am using binsearch.com

I have discarded Thunderbird as client because Thunderbird did not work well for me when it comes to usenet. 
Tried Newsbin running under wine but that is unstable so not usable for me.

Is there **a great news reader client that runs smooth in linux?** That let me search giganews and also free usenets?

---

### Post by oldos2er on 2009-11-29
> **slope said:**
> The only thing I now need is a really easy to use **news reader client** so I can find what I need to download.

 Pan. To install it, run **sudo apt-get update && sudo apt-get install pan** in a terminal.

---

### Post by slope on 2009-11-29
Thx. Hmm. Pan was not easy going. 
It seems I spend lots of bandwidth loading headers in large groups.
And when finally loaded its hard finding what I need the nzb file.

Maybe I am doing something wrong here? Have anyone seen Pan tutorial online?
Or a video tut? So many people speaks warmly about Pan so I reckon I must be at fault here. 

Btw, is there an easy config file I can edit to make hellanzb start up each boot? Never done a thing like that in ubuntu and feddeling around I saw two places it could have worked but I could not figure out neither: 
**Application -> System -> Services** 
nor
**Application -> Settings -> Settings Manager -> Autostarted Apps**

Either I overlooked something or there is a txt config file somewhere that I can edit, right?

---

### Post by slope on 2009-11-30
**Update:**

Well that hellanzb has now driven me inzane....
Worked like a charm first, then suddenly all nzb added was queued.
Parsed one then queued them all. No more fun :-(

I searched and used the well proven trial%error method, yet still not running. First it seemed it was due to spaces in group name for the usenet groups. So made changes according to post i found:

I edited the file /usr/share/python-support/hellanzb/Hellanzb/NZBLeecher/Protocol.Py and right below line 513 I added:

```

group = group.strip()
```

Then in another post I found that the first one did not actually solve me problems so I I continued the work.

```
def gotGroup(self, group):
        group = group[3]
        group = self.gettingGroup
        self.activeGroups.append(group)
        self.gettingGroup = None
        debug(str(self) + ' got GROUP: ' + group)

```

I'll seen posts back to 2007 with the same issues, one should think a popular app like hellanzb would have overcome such problems in two years. That leads me to think that even if I'll seen people with same errors I might not have the same cause as them as long as correcting what they did ended up not solving my problems.

Any clues what to do now?

---

### Post by slope on 2009-11-30
Ok spending countless hours searching for en error I finally did the sensible thing and **uninstalled Hellanzb and Pan.**

What was becoming more and more clear for me was to totally drop newsreader client, at least for the time being. Usenet learning curve is steep enough without having to deal with the hazzle with a newsreader and enormous headers from groups eating your bandwidth.Rather I would recommend using one of the sites where you can download the NZB file. They have search capabilities, gives you an easy to use UI but some might charge you a few $ for membership. I return you get longer retantion.


After I uninstalled:

```
sudo apt-get remove *program name here*
```

I decided to give Hellanzb one more go, as it worked for me in the forost place. Strangely clean install with the same config file from earlier worked like a charm. 

Now I am using that bandwidth again.

---

### Post by slope on 2009-12-04
Just a tiny update:

SSL working flawless. Turns out when using SSL use port 443 rather then 119 with giganews and a few others. 

Hellanzb working great now. No need to struggle with 100 or so files, par , rar and what not. Hellanzb takes care of it all.

Btw I came over this site, [great how to tutorial for hellanzb install on ubuntu.]("http://www.adamsmash.com/?p=228&cpage=1#comment-128")

If things goes wrong for some reasson the trick that did it for me was actually removing it and starting over with a fresh install.

---

