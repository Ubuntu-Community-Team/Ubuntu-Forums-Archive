---
title: "Google Chrome - Your profile could not be opened correctly"
date: 2010-08-11
forum: General Help
---

### Post by Cant on 2010-08-11
Lately I've been getting this error whenever I start google chrome (only when another instance of Chrome is not running, though)

[img]http://farm5.static.flickr.com/4101/4882888729_14be0eaef6_z.jpg[/img]

"Your profile could not be opened correctly. Some features may be unavailable. Please check that the profile exists and you have permission to read and write its contents."

What is this and how can I fix it?

---

### Post by Brandon Williams on 2010-08-12
Your google-chrome profile can be found in ~/.config/google-chrome/. To determine whether there are any files or directories there that you cannot read or write, use this command:
```
find ~/.config/google-chrome ! -perm -u+rw
```

You might also want to determine whether there are any directories that are not executable:
```
find ~/.config/google-chrome -type d ! -perm -u+x
```


To fix the problem, you will need to use chmod to add read/write permission to any file/dir that is missing these permissions, and add execute permission to any directory that is missing it, i.e.:
```
chmod u+rw filename
chmod u+rwx dirname
```

---

### Post by eromana on 2011-10-24
From Ubuntu 11.04 and Chrome 12.0.742.112-r90304
Both 
-$ find ~/.config/google-chrome ! -perm -u+rw  
-$ find ~/.config/google-chrome -type d ! -perm -u+x  
do not find any any files or directories without read, write, or execute permissions 
- but still, the first time Chrome is invoked, I get the 'Your profile could not be opened...' msg

---

### Post by eromana on 2011-10-24
Using a SOLVED solution example from a Chromium post,
Open the home folder,  copy and paste into the address ruler  
~/.config/google-chrome  
Open that directory, rename the Default directory to Default-bk 
Close and open Chrome. A new Default directory is created. Open it and delete the bookmarks file. 
Open the Default-bk directory copy the bookmarks file there and paste it into the Default directory.

---

### Post by oldos2er on 2011-10-24
Closed, please don't bump old threads. If you have a question or problem please start a new thread.

---

