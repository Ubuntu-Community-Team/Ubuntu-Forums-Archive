---
title: "E: Type '&#8220;deb' is not known on line 1 in source list /etc/apt/sources.list"
date: 2010-04-22
forum: General Help
---

### Post by facsimile on 2010-04-22
hey guys!!! i need help my 1st weekin ubuntu and i already did something bad!!!

i cant update, watch videos, listen to music and flash app in the web wont work, and i cant update anythig.
if i do it in the terminal i get this "sudo apt-get update"

E: Type '&#8220;deb' is not known on line 1 in source list /etc/apt/sources.list

what do i do?:confused::confused:

i would really apreciate it if somebody can help me!!
big thanks:)

---

### Post by aysiu on 2010-04-22
Paste this command into [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
cat /etc/apt/sources.list
``` and then past the output back here.

---

### Post by facsimile on 2010-04-22
&#8220;deb [http://archive.offensive-security.com](http://archive.offensive-security.com) pwnsauce main microverse macroverse restricted universe multiverse&#8221;

this is what came up?

---

### Post by aysiu on 2010-04-22
> **facsimile said:**
> &#8220;deb [http://archive.offensive-security.com](http://archive.offensive-security.com) pwnsauce main microverse macroverse restricted universe multiverse&#8221;

this is what came up?
Those quotation marks shouldn't be there.

Paste this command in ```
gksudo gedit /etc/apt/sources.list
``` This will open up the sources.list file in a text editor.

Delete the **"** marks at the beginning and the end of the first line.

Save the file and exit.

Then ```
sudo apt-get update
```

---

### Post by 3rdalbum on 2010-04-22
In future, when you want to add new repositories to your package management system, use the "Third-Party" tab in System > Administration > Software Sources, rather than just directly modifying the /etc/apt/sources.list file.

If you use the Software Sources program to edit your repositories, it prevents mistakes like yours.

---

### Post by facsimile on 2010-04-22
aysiu thanks i dont get the "Re: E: Type '&#8220;deb' is not known on line 1 in source list /etc/apt/sourc" anymore

but i still cant update i get..

Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch [http://archive.offensive-security.com/dists/pwnsauce/Release](http://archive.offensive-security.com/dists/pwnsauce/Release)  Unable to find expected entry  main/binary-amd64/Packages in Meta-index file (malformed Release file?)



i got the problem by trying to install a backtrack aplication.. and in the terminal i get


Fetched 23.0kB in 3s (5,964B/s)
W: Failed to fetch [http://archive.offensive-security.com/dists/pwnsauce/Release](http://archive.offensive-security.com/dists/pwnsauce/Release)  Unable to find expected entry  main/binary-amd64/Packages in Meta-index file (malformed Release file?)

E: Some index files failed to download, they have been ignored, or old ones used instead.


thanks for all your help

---

### Post by aysiu on 2010-04-22
Sounds as if you're using 64-bit Ubuntu and offensive-security's software repository doesn't have software for 64-bit (only 32-bit, probably).

**Edit**: Yeah, all I'm seeing here is i386:
[http://sun.backtrack-linux.org/dists/pwnsauce/](http://sun.backtrack-linux.org/dists/pwnsauce/)

---

### Post by facsimile on 2010-04-22
i do have the 64 bit ubuntu..

but how can i get it to be nomal again?
and find the updates for ubuntu no offensive security?

---

### Post by JoelOl75 on 2010-04-22
Remove the line from the sources list referring to [http://archive.offensive-security.co...nsauce/Release](http://archive.offensive-security.co...nsauce/Release)

---

### Post by facsimile on 2010-04-22
thanks!!! it did help..

is that why i cant watch movies or play mp3s?

because it dosent find the plugins.

---

### Post by JoelOl75 on 2010-04-23
you need to install the medibuntu repository.  Go to [http://www.medibuntu.org](http://www.medibuntu.org) and follow the repository how-to. Then you can add the libdvdcss2 package to watch dvd's and also add the ubuntu-restricted package for all the codecs for audio and video.

---

### Post by aysiu on 2010-04-23
You don't need to add Medibuntu to get *ubuntu-restricted-extras*

You do need it for *libdvdcss2* and some other stuff, though.

More details here:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

