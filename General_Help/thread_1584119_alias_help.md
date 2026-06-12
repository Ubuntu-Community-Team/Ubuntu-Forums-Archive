---
title: "alias help"
date: 2010-09-28
forum: General Help
---

### Post by cmcanulty on 2010-09-28
I run the following script at our library to update the Ubuntu machines. I want to totally automate it for when I am not there. So what I would like is to automate the  -y so it doesn't stop and have to enter y or n. This is the code I use now,
```
alias ud='sudo apt-get update && sudo apt-get upgrade && sudo apt-get clean'
```
Would this be the correct form? Or should the -y be somewhere else in the code? I am aware that this confirms all updates  and that is OK.
```
alias ud='sudo apt-get update && sudo apt-get upgrade && sudo apt-get clean -y'
```

---

### Post by Tylerjd on 2010-09-28
> **cmcanulty said:**
> I run the following script at our library to update the Ubuntu machines. I want to totally automate it for when I am not there. So what I would like is to automate the  -y so it doesn't stop and have to enter y or n. This is the code I use now,
```
alias ud='sudo apt-get update && sudo apt-get upgrade && sudo apt-get clean'
```
Would this be the correct form? Or should the -y be somewhere else in the code? I am aware that this confirms all updates  and that is OK.
```
alias ud='sudo apt-get update && sudo apt-get upgrade && sudo apt-get clean -y'
```

Well, to start, and this is optional if you want to run it on a regular basis, you are going to want to run it as a cron job as root, so it won't ask for any password and it will not have any sort of user prompt, wether command line or not (all though, this could be dangerous, as it *is* running as root)(and you probably will not need the sudo if you are to do that as sudo just makes you SuperUser for that task).

Next, you had the right idea, using -y but you will need to use
```
sudo apt-get update && sudo apt-get upgrade -y && sudo apt-get clean -y 
```

As I said, if you run this job as cron root, then you probably will not need the sudo, and if you also want to update the kernel while running this, if there are any kernel updates available, you will wan to run: 
```
sudo apt-get update && sudo apt-get upgrade -y && sudo apt-get dist-upgrade -y && sudo apt-get clean -y
```

---

### Post by cmcanulty on 2010-09-29
If I run it as a cron will the computer user have to type the password each time it runs? The reason I ask is that I do all the admin in the librarian account, but the people who use the account are limited user with a Library user account.Also does the dist-upgrade do the new OS like to 10.10 when it comes out? Because that takes a long time and I wouldn't want that to start unless I plan for the extra time the machines would be tied up. Thank you. I am really working with people at the library that have trouble figuring out things like is it plugged in or where are my Documents.

---

