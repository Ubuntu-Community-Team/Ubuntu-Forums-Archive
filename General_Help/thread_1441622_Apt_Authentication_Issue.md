---
title: "Apt Authentication Issue"
date: 2010-03-29
forum: General Help
---

### Post by dmzamora on 2010-03-29
[FONT="Trebuchet MS"]A few days ago when I updated my Ubuntu 9.10 this came out:

Apt Authentication issue 
 
Problem during package list update. The package list update failed with a authentication failure. This usually happens behind a network proxy server. Please try to click on the "Run this action now" button to correct the problem or update the list manually by running Update Manager and clicking on "Check". 

After I ran the update

This error appeared:

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com> 
 
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/Release](http://security.ubuntu.com/ubuntu/dists/karmic-security/Release)   
 
W: Some index files failed to download, they have been ignored, or old ones used instead. 


Any idea how I can fix this?[/FONT]

---

### Post by gmargo on 2010-03-29
A very common error.  Recently discussed over here: [http://ubuntuforums.org/showthread.php?t=1438361](http://ubuntuforums.org/showthread.php?t=1438361).  See post #3 on that thread for a probable solution.

---

### Post by dmzamora on 2010-03-29
@gmargo

Thanks!  I will try this tonight and update what happens.:wink:

---

### Post by dmzamora on 2010-03-31
Hi!  The issue that I reported has been resolved, however not using the instruction you gave me @gmargo.

I tried what you instructed me to do but still, the same error appeared and more.

A friend read the error report and suggested that I do the following:

sudo apt-get autoremove
sudo apt-get update

Then it updated itself! ;-)

I hope it won't get the same error anymore.

Thanks for the idea though.

---

