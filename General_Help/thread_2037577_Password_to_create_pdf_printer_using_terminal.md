---
title: "Password to create pdf printer using terminal"
date: 2012-08-04
forum: General Help
---

### Post by jayrwv on 2012-08-04
Ubuntu noob. I am trying to creat a pdf printer. I am told to go to "Terminal" and enter sudo apt-get install cups pdf.

I do that and it asks for a password. The only password I know is the one I used to create ubuntu in the first place. 

I cannot figure it out. Can someone direct me, please?

---

### Post by efflandt on 2012-08-04
You just use the password you logged in with.

However, you should make sure you spell a package properly.  You are missing a hyphen.  It should be:

```
sudo apt-get install cups-pdf
```

---

### Post by jayrwv on 2012-08-04
Thank you efflandt. I can not believe I missed that hyphen. It worked.  Thanks very much.

---

