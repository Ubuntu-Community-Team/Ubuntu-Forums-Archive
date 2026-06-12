---
title: "How do I remove the user list in gdm login for Ubuntu 10.04"
date: 2010-07-27
forum: General Help
---

### Post by deserthowler on 2010-07-27
In Ubuntu 9.10 I was able to remove the user list from gdm.  However in 10.04 I am unable to do this.  I searched the forums with no luck.  
I opened gconf-editor using sudo and went to apps>gdm>simple-greeter.  I then checked disable_user_list.
After complete shutdown, I was still placed in the list screen.  I checked gconf-editor and the disable_user_list was still checked.
Any suggestions?

Earl

---

### Post by sisco311 on 2010-07-27
You have to change the value of the key as user gdm (not as root).

Disable the face browser: 
```
sudo -u gdm gconftool-2 --set --type boolean /apps/gdm/simple-greeter/disable_user_list true
```

Enable the face browser: 
```
sudo -u gdm gconftool-2 --set --type boolean /apps/gdm/simple-greeter/disable_user_list false
```

---

### Post by deserthowler on 2010-07-27
That didn't work for me.  

Earl

---

### Post by deserthowler on 2010-07-27
Well, this time I shutdown and restarted and it worked.  
Thanks,
Earl

---

