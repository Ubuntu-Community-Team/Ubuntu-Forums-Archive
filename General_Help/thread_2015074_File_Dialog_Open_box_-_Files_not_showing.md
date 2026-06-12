---
title: "File Dialog Open box - Files not showing"
date: 2012-07-02
forum: General Help
---

### Post by varzues on 2012-07-02
In 12.04 trying to setup a openvpn connection through the configure tool and the file dialog box to link in certs and other files doesn't actually see the files in the directory.

I've double checked the files, have values and are the right extensions, aren't hidden or anything goofy that I noticed. I can see and interact with them in the CLI/File system.

Anyone have any suggestions or ideas?

---

### Post by ubudog on 2012-07-02
Hi, could you post a screenshot of what's happening?

---

### Post by varzues on 2012-07-02
Excuse my poor circles, they're rough to draw on a laptop.:rolleyes:

---

### Post by ubudog on 2012-07-03
Try clicking on the "PEM or PKCS#12 certificats (*.pem, *.crt, *.key, *.cer, *.p12)" file type dropdown in the dialog box.  Are there any more options?

---

### Post by varzues on 2012-07-03
Unfortunately not, the option displayed is the only option.

---

### Post by cipherboy_loc on 2012-07-03
Two things: 
1) Can you drag and drop the files?  
2) Check the permissions on the files, though that shouldn't stop them from showing in the file manager. 


Cipherboy

---

### Post by varzues on 2012-07-03
Dragging and dropping did work. The files have a 664 permission set(-rw-rw-r--) and user:group are correct as well.

Thanks for the suggestion! 

I'm not entirely sure the files weren't corrupt from a dropbox incident (the evening before I attempted this my files were corrupted in dropbox all file contents removed and file sizes reduced to 0. Had to restore them all). I'll grab a copy of the file from the ubox @ work and see if they act the same way.

---

