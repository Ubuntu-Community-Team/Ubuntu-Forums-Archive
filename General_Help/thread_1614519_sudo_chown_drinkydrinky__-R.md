---
title: "sudo chown drinky:drinky * -R"
date: 2010-11-05
forum: General Help
---

### Post by nooodles on 2010-11-05
Short version:
Winxp box with dying hard drive.
Salvaged files via running live CD / file transfer via LAN.

The saved Files have no owner.
I did:
```
sudo chown tom:party * 
```This did not get the sub-directories or the sub-directories sub-directories etc..
so I screwed up and ran:
```
sudo chown tom:party * -R
```now the folders are listed as files.
I do not know how to reverse this as  I screwed up the command with a careless 'DOS habit of tags at the end...   ](*,)

---

### Post by nooodles on 2010-11-05
Resolved....

I didn't know how to proceed.. so I just screwed around anyway and using the GUI
My permissions were set to -> read, list, no access
I changed them to create & delete and clicked to apply these permissions to the enclosed files.
Everything is back...

I don't understand just what happened - why the subdirectories because listed as a file instead of a folder...
but this time just screwing around solved it for me.

Thanks to anyone who read this and/or responded while I typed this up. 

Now to figure out how to mark this thread as solved :popcorn:

---

### Post by wilee-nilee on 2010-11-05
> **nooodles said:**
> Resolved....

I didn't know how to proceed.. so I just screwed around anyway and using the GUI
My permissions were set to -> read, list, no access
I changed them to create & delete and clicked to apply these permissions to the enclosed files.
Everything is back...

I don't understand just what happened - why the subdirectories because listed as a file instead of a folder...
but this time just screwing around solved it for me.

Thanks to anyone who read this and/or responded while I typed this up. 

Now to figure out how to mark this thread as solved :popcorn:

Nothing like figuring it out yourself.;) solved is in thread tools you have to be logged in to see this.

---

