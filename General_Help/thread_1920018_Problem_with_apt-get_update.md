---
title: "Problem with apt-get update"
date: 2012-02-03
forum: General Help
---

### Post by Clopper Almon on 2012-02-03
When from a terminal window I do

sudo apt-get update

I get many lines like these two


Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/restricted Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/universe Translation-en

and then:

*******

Fetched 72 B in 1s (44 B/s)
Reading package lists... Done
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/oneiric/Release](http://extras.ubuntu.com/ubuntu/dists/oneiric/Release)  

W: Some index files failed to download. They have been ignored, or old ones used instead.

********

If repeated, the results are the same, so I think the repository is in fact not updated.

Any help would be appreciated, or even just knowing that I am not alone.

---

### Post by jerrrys on 2012-02-03
This is a GPG error fix you can try.

sudo -i
apt-get clean
cd /var/lib/apt
mv lists lists.old
mkdir -p lists/partial
apt-get clean
apt-get update

---

### Post by williejones on 2012-02-03
Try this

sudo -i 
apt-get clean 
cd /var/lib/apt mv lists lists.old 
mkdir -p lists/partial 
apt-get clean 
apt-get update

Ooops got beat by jerrrys post

---

### Post by Clopper Almon on 2012-02-04
Many thanks to both of you.

I searched further and found this post by Azend. I tried it and it worked nicely. I think it is similar to your suggestions.


# First delete all of the previously available listings
[FONT="Courier New"]sudo rm /var/lib/apt/lists/* -vf
[/FONT]
# And then use apt-get to rebuild your package listings
[FONT="Courier New"]sudo apt-get update[/FONT]

---

### Post by jerrrys on 2012-02-04
Good call Clopper

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

Edit: no it wont; edited out

---

