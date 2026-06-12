---
title: "Unable to upgrade to 12.04 from 10.04"
date: 2012-05-10
forum: General Help
---

### Post by KarmicBuddy on 2012-05-10
Hi,

I have applied all the latest updates to my 10.04 and done exactly as said in release notes of 12.04 to help me upgrade to it. But in spite of all this, the only thing shown by the update manager is "New release 10.10 available".
Why is it not showing 12.04 ?

---

### Post by 2F4U on 2012-05-10
Are you sure that your system is up-to-date? In your screenshot I read "The package information was last updated 174 days ago".

---

### Post by wilee-nilee on 2012-05-10
10.04.1 is a long term release so is 12.04.1, even though it has been released the final release is in July, and when it will officially show up in your update manager. You can run a command though to get it to show up now. 

Some advise to wait.

What ever you do make sure you are backed up well enough to take a complete fail. I'm not saying this will happen, but always be prepared.

---

### Post by TBABill on 2012-05-10
Could you update via terminal by ```
sudo apt-get update
```Then go to update manager and see if it offers you 12.04. You may need to tell it to show you only LTS versions since it thinks 10.10 is still an option.

---

