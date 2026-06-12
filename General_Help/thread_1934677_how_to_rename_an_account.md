---
title: "how to rename an account"
date: 2012-03-02
forum: General Help
---

### Post by olwe on 2012-03-02
I recently cloned my drive for another identical machine. Now the new machine has exactly the same U11.10 installation. Q: how can I change the account name? I want to give this new machine to my son and have his user name/password, i.e., /home/dad should be /home/son1

---

### Post by imachavel on 2012-03-02
so you captured the image with a disk that captured the image from a bios, with a program made to do so, is it called dual copy or x copy? I forget the name

I'm surprised you figured out all that but are stuck on what account information needs to be renamed. Give me one second...


usermod -l danel@danel-Dimension-4700 danel@danel-Dimension-4700
usermod: user 'danel@danel-Dimension-4700' does not exist

I thought the command usermod -l would work for me. Maybe I didn't type the old name correctly, but anyway wanted to type the new name in anyway. I am very surprised it didn't ask me for my password, maybe if the name had been correct, it'd say "you must be root to do that!", in which case sudo usermod -l would work better. give it a shot, play with it, tell me if it works, I am keeping my current user name though

---

