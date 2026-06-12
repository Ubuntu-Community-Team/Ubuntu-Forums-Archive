---
title: "File Organization Help for Newbie"
date: 2010-05-10
forum: General Help
---

### Post by milan_b on 2010-05-10
So I downloaded Celtx, and extracted the .tar.bz2. I did ./celtx from the command line in the celtx directory, and Celtx runs.

My question is, is it a good idea to put the celtx folder into /usr/lib or should I put it somewhere else? I just use sudo mv celtx /usr/lib right?

Also, is there any point in hanging onto .deb files that were already used?

Thanks

---

### Post by mb_webguy on 2010-05-10
The standard locations for locally installed software are /usr/local/bin, /opt, and a bin directory in a user's home directory (though the latter is generally for personal scripts, not full applications).  If your archive just contains a script or binary executable, you could put it in one of those locations -- I'd suggest /usr/local/bin.  Just make sure to use chown and chmod to make sure the ownership and permissions are correct.

---

### Post by milan_b on 2010-05-10
Sorry this is probably a stupid question... Who should own it (you mean the folder right?) and what permissions are correct?

---

