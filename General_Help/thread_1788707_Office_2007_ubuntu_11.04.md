---
title: "Office 2007 ubuntu 11.04"
date: 2011-06-23
forum: General Help
---

### Post by JAS510 on 2011-06-23
Hello,

I just loaded office 2007 on my admin account, but when I switch users, I am unable to see the Office 2007 suite.  The only thing i see is the Note pad under accessories.  

I have ubuntu 11.04.. Installed the latest version of Wine.  I'm sure its a permission settings.  

thanks

JAS510

---

### Post by life in color on 2011-06-23
hmmmm....have you tried installing Office and Wine on the seperate account? the '.wine' hidden folder is located within whatever user directory its been installed on so it makes since that it would only work on the account it was installed on.

---

### Post by JAS510 on 2011-06-23
So if I wanted all my users (3 users) to be able to run office applications, I would have to load it again on every user's profile?

---

### Post by life in color on 2011-06-23
That's what I'm thinking no guarantees but it seems like the only way to go, you may want to google something like "linking WINE to all accounts" or something. You could try manually copying your .wine folder to the other accounts but I wouldn't recommend this at all.

---

### Post by Mark Phelps on 2011-06-23
You also need to do two other things ...

First, you need to go to the winehq website and search through their application compatibility database for the Office components and versions you want to use.  You will see that some of them have very low ratings -- which means they are NOT going to work in Wine, no matter what you do.

Second, you need to go to the Wine subforum here and look through that.  Someone there may have already addressed the problem you're having.

---

### Post by JAS510 on 2011-06-23
Ok thanks guys

---

