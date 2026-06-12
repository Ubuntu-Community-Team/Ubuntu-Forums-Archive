---
title: "setting up shares for non-user owned folders"
date: 2010-03-11
forum: General Help
---

### Post by gmushial on 2010-03-11
I've setup a Moodle server on 9.10 server, and have been able to share user folders back to the windoze machines on the home net. What I'd like to do is share the Moodle main folder (and descendents) likewise. The problem is that it's owned by root. For ther user folders, as long as the owning user was logged in they were able to mark the folder as shared and everything worked very smoothly. When I try to mark the moodle folder as shared, no suprise I get a permission error. Is there a way of doing a "sudo su" from the GUI desktop to allow this to happen? Or do I have to set up the share from a command line (after having done a sudo su)? Can anyone give me the magic commands needed to do such? Or, can someone point me to the documentation to do such?
many thanks,
greg

---

### Post by dcstar on 2010-03-11
> **gmushial said:**
> 
Is there a way of doing a "sudo su" from the GUI desktop to allow this to happen? Or do I have to set up the share from a command line (after having done a sudo su)? Can anyone give me the magic commands needed to do such? Or, can someone point me to the documentation to do such?


You can install the **nautilus-gksu** package to give you an option of opening anything with root privileges.

---

