---
title: "Nautilus not sharing"
date: 2010-03-05
forum: General Help
---

### Post by odsus1 on 2010-03-05
Hello all, So I heve two ubuntu boxes that until recently have been playing nice together, I use one as storage (Karmic) and one as a media center (hardy media).  I am using Rhythmbox to play music over my network, now all of a sudden my shares dont work, so I go to my Karmic box and open up Nautilus from the terminal and I get this:

"odsus1@linux-main:~$ sudo nautilus
[sudo] password for odsus1: 

(nautilus:27203):  Eel-CRITICAL **: eel_preferences_get_boolean: assertion  `preferences_is_initialized ()' failed
Initializing nautilus-gdu  extension

** (nautilus:27203): WARNING **: No marshaller for signature of  signal 'UploadFinished'

** (nautilus:27203): WARNING **: No  marshaller for signature of signal 'DownloadFinished'

**  (nautilus:27203): WARNING **: No marshaller for signature of signal  'ShareCreateError'
Shutting down nautilus-gdu extension

--- Hash table keys for  warning below:
--> root
--> inode/directory
--> l2069
-->  l2049

(nautilus:27203): Eel-WARNING **: "unique eel_ref_str"  hash table still has 4 elements at quit time (keys above)

(nautilus:27203): Eel-WARNING **: "nautilus-directory.c:  directories" hash table still has 4 elements at quit time"

My shares are all enabled but when I try to acces the Karmic box on the Hardy one I get an error saying **Unable to mount location** Failed to retrieve share list from server. 

So my question is; What is going on here?

Thanks, Odie

---

