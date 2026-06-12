---
title: "&quot;Failed to Fetch&quot; error message when trying to update from the Terminal"
date: 2011-11-25
forum: General Help
---

### Post by HunterDX77M on 2011-11-25
Recently, when I run
```
sudo apt-get update
```

I get this towards the end of the output:
```

Err http://ppa.launchpad.net maverick/main i386 Packages                       
  404  Not Found
.
.
.
W: Failed to fetch http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/maverick/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

I don't know much about repositories or anything like that, but I am pretty sure I don't need stuff from Maverick as I am running Natty. Any suggestions?

---

### Post by dcstar on 2011-11-26
> **HunterDX77M said:**
> Recently, when I run
```
sudo apt-get update
```

I get this towards the end of the output:
```

Err http://ppa.launchpad.net maverick/main i386 Packages                       
  404  Not Found
.
.
.
W: Failed to fetch http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/maverick/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

I don't know much about repositories or anything like that, but I am pretty sure I don't need stuff from Maverick as I am running Natty. Any suggestions?

Remove it from the Repository list.

Why are you using the command line when the Update Manager or Synaptic do this function?

---

### Post by mörgæs on 2011-11-26
You are doing it correctly. Using the command line often gives better error messages.

As stated above, removing references to older versions in sources.list is the solution.

---

### Post by dcstar on 2011-11-26
> **mörgæs said:**
> You are doing it correctly. Using the command line often gives better error messages.
........

Rubbish, the GUI tools exist to allow users not to use arcane command line strings because most **normal** people do not want to have to deal with that sort of rubbish.

Synaptic and the Update Manager display all the error information anyone needs in this situation.

People insisting on using the command line display the attitude that has held back Linux from the mass market for decades now.

---

### Post by HunterDX77M on 2011-12-14
> **dcstar said:**
> Rubbish, the GUI tools exist to allow users not to use arcane command line strings because most **normal** people do not want to have to deal with that sort of rubbish.

Synaptic and the Update Manager display all the error information anyone needs in this situation.

People insisting on using the command line display the attitude that has held back Linux from the mass market for decades now.

I use the command line to better learn it. I know that there is a perfectly easy solution by just using the GUI, but I am trying to practice using the command line, that's all.

Also, how would I go about removing the repository (either via command line or GUI)?

---

### Post by HunterDX77M on 2011-12-14
Here's a screenshot of where I think I should be. I don't see any maverick stuff here, though.

---

### Post by mörgæs on 2011-12-14
Then look a little closer...

---

### Post by HunterDX77M on 2011-12-17
> **mörgæs said:**
> Then look a little closer...

Well, don't I feel stupid. :)

Okay, I got rid of it, but should it affect whether or not my Flash updates correctly in the future?

---

### Post by mörgæs on 2011-12-17
Yes, mixing different versions in the sources.list file is messing things up. 

Here is a link to a sources.list generator:
[http://repogen.simplylinux.ch/index.php](http://repogen.simplylinux.ch/index.php)

---

