---
title: "Moving /home partition with Psychocats tutorial... with a twist"
date: 2009-10-30
forum: General Help
---

### Post by Chonnawonga on 2009-10-30
I'm working on moving a /home partition, using this tutorial from Psychocats: [http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome")

The trick is, I don't want to move everything, only most of it. I want to leave the /home/videos directory behind. Is there any way to execute this command
```
find . -depth -print0 | cpio --null --sparse -pvd /new/
```
while ignoring one directory?

---

### Post by Giblet5 on 2009-10-30
> **Chonnawonga said:**
> I'm working on moving a /home partition, using this tutorial from Psychocats: [http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome")

```
sudo bash ### DANGEROUS!!! ENTER COMMANDS EXACTLY!
cd /home
find . | grep -ve '^./videos' | cpio -o | (cd /new ; cpio -iv)
exit
```


That should do it.

---

### Post by Giblet5 on 2009-10-30
How *I* would do it
```
sudo bash ### DANGEROUS!!! ENTER COMMANDS EXACTLY!
cd /home
tar -cpf - . --exclude="./videos/" | (cd /new ; tar xvpf -)
exit
```

---

### Post by Chonnawonga on 2009-10-30
OK, thanks... on both counts!

Now, I have to ask, why would you use the second command rather than the first? And I assume the second would copy all permissions and ownership properly, right?

---

### Post by Giblet5 on 2009-10-30
> **Chonnawonga said:**
> OK, thanks... on both counts!

Now, I have to ask, why would you use the second command rather than the first? And I assume the second would copy all permissions and ownership properly, right?

I like tar and it's always there while cpio's an option on some systems... Both will do exactly the same thing - copy everything - files, permissions, links, timestamps... Everything.

---

### Post by Chonnawonga on 2009-10-30
Thanks, Giblet5! You've saved me a ton of time and trouble!

---

