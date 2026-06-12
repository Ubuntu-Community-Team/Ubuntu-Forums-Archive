---
title: "Selecting certain file types by extension"
date: 2011-03-06
forum: General Help
---

### Post by danjahner on 2011-03-06
I am trying to move files from one folder to another based on their file extension. I can do it with a single extension, but I want to match multiple.  

Example: 

find /home/user/bulkfiles -type f -name "*.mov" -a -print | xargs -I{} mv {} /home/user/sortedfiles/videos

This works, but I want it to not only match mov, but also mpg, flv, mp4, etc. I would think something like [mov,mpg,flv] would work, but it doesn't.

---

### Post by alphaamanitin on 2011-03-06
To move mulitple file types I just string commands together.  Might be an easier way but I don't know one:

```
mv /home/*.jpg /home/Pictures; mv /home/*.png /home/Pictures; and so on
```


I wonder if something like this would work: 

```
 mv /home/*.(jpg|png|tif) /home/Pictures
```

AlphaA

---

### Post by jrtayloriv on 2011-03-06
To move all of the extensions at once, you can do this:

**> find /home/user/bulkfiles -type f \( -name "*.mov" -o -name "*.flv" -o -name "*.mp4" \) | xargs -IFILES cp FILES /home/user/sortedfiles/videos**

This will copy all .mov, .flv, and .mp4 files found below **/home/user/bulkfiles** into **/home/user/sortedfiles/videos**

---

### Post by alphaamanitin on 2011-03-06
> **jrtayloriv said:**
> To move all of the extensions at once, you can do this:



This will copy all .mov, .flv, and .mp4 files found below **/home/user/bulkfiles** into **/home/user/sortedfiles/videos**


I knew there was a way to do this.  

AlphaA

---

### Post by danjahner on 2011-03-06
Perfect. Thanks for your help.

---

