---
title: "Update information is outdated"
date: 2011-11-29
forum: General Help
---

### Post by pgrim91 on 2011-11-29
Hello, I have 11.10 running on an Asus and the red triangle letting me know my update information is outdated has been up for about a week.  I do as it says and manually check for updated - nothing fails.  I try to check in the preferences dialogue and nothing seems out of ordinary in terms of software sources, plus I still get updates for nearly everything else on my system.  I looked around a bit on the forum and didn't find any solution for the problem, mostly the triangle has been caused by a project that lost support with the newest version or things like that.  I even made sure the opera browser software sources were unchecked.  So am I just not looking in the right place for the update error, or is there something else I missed?  Either way I'd just like to remove the red triangle

Thanks

---

### Post by bluexrider on 2011-11-29
did you try right click in the icon and refresh? If that doesn't work try 

sudo apt-get update && sudo apt-get upgrade

---

### Post by pgrim91 on 2011-11-29
here we go, this is the error:

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/oneiric/Release](http://extras.ubuntu.com/ubuntu/dists/oneiric/Release)  

W: Some index files failed to download. They have been ignored, or old ones used instead.
-----
So should I just uncheck the extras.ubuntu source?  I honestly don't know what software gets updated from there

---

### Post by bluexrider on 2011-11-29
Try this:
  sudo -i 
apt-get clean 
cd /var/lib/apt 
mv lists lists.old 
mkdir -p lists/partial 
apt-get clean 
apt-get update

---

### Post by pgrim91 on 2011-11-30
okay, that appears to have worked as there was not an error message and the red triangle went away, lets give it a few days and see if it comes back . . .

Thanks so much bluexrider!

---

### Post by bluexrider on 2011-11-30
please mark this (SOLVED)

---

