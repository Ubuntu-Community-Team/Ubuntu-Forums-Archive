---
title: "Trying to set up homebrew &quot;cloudtop&quot; client systems"
date: 2011-06-26
forum: General Help
---

### Post by draco.red on 2011-06-26
Hello all; I'm currently working on a project to roll out some custom cloudtop / internet appliance systems and was running into a few snags and was just wondering if anyone could offer suggestions.  

The current plan is to roll out a few hundred Intel Atom Mini ITX boxes to remote locations with customized *nix install on a 16GB USB flash drive as the only local storage.  The idea is that all information would be stored on our central SFTP file server.  The end result we're hoping for would be that end user would log in on the box and it would load their user profile onto the system ( basically browser profile, address book and IMAP settings for email program).  After that everything would be mapped to the file server as a network mount location.  

This is relatively simple to implement with a few startup scripts; but given that some of the remote locations will be on some really slow internet connections (256Kbps; best they can get out in the middle of nowhere) the latency for uploading and downloading anything they need to access would start to really bite into their time.  That and since there is 16GB accessible on the local system (minus OS overhead) and few users would go over that it would make sense to set up some sort of local caching.  

So I'm sort of stuck on that; needs to be instantly backed up on the remote server and have transparent box-to-box portability and needs to account for the few users that would go over the amount of space they have locally.  And I've been racking my brain (and my google-foo) to figure out how to implement; but everything I come up with breaks at least one of those criteria to some extent.  I'm sure that there are some services out there that would be able to take care of the back end of this for us, but the higher ups are insistent that we not rely on any third party services for this project.

TL;DR I'm looking to make CromeOS without using the Googles, how I do? [sic]

---

