---
title: "Strange folder names in root directory"
date: 2009-09-12
forum: General Help
---

### Post by itsjareds on 2009-09-12
I've got about 20 folders in my root directory that all are named strangely, like they are hashes. Here's my root dir:

```
jared@jared-desktop:/$ ls
0005f85fae4544979d                cdrom
07eab8370d16d4fa05f9b4500758d8a2  d64e27487d2301d156852a77fd23fa
0be48d63807cc2841fec6e84          da91dc72914004b08f1b3f
1404a28cab475f67b1c227a15c        dbefb39ca94bc1050eb79b63
14fb919108746974b4eac4e23b        dev
1894405853b46bd579                e1e5dce6daf30ba562a8
281c578a0db39ac40f                e66b0d46894ef6a3bb81fc4d0f0e0b
38064925bb0dd7610a                etc
3972ba76730c261cfd5f              f181f431378abe42cb94
405635960fa4429fef                fe3b219e9812188a00a9dd00585623
4061816627991e89f1                ff3df5221840025adb2aac91128e9476
443faf2419827bec5141723317        ff6914b58feaebf5a956b62dc9a220e5
46c5ffc4eba28e8508e80adb02a480    home
47971529d6333735d65444c7dd21ce90  initrd.img
4ce32926a6d3b29a7deac2c59f        lib
59f6888911dca53b5cee              lost+found
5ace4b0a06e07f3aa0ac1c            media
5e2bdbedf76f5f6abfe1ad979a558b    mnt
71464410d07707edc9f9              opt
745923c0525ce0be82f65c61ba        proc
81828ac276c4df52802f              Recycled
98fa07497d81372e15                root
9fd0dff3ed195815430f79ce07396694  sbin
a11aab64de3ada9218aa              selinux
a23417efb0f8f9791ccce4            srv
a8a36f1052d8c8e438                sys
aad030ecf46678c8f362e4            tftpboot
b9f0f87ae9b89451f9e2              tmp
bbaeda40b88fcae4f0a072e9          usr
bin                               var
boot                              vmlinuz
c5f0ae3a91c8ffb28f41a36a626e
```

What are all of those hashed names? They look vaguely like GUIDs, but they also look like those annoying folders that Windows will place sometimes. I have a gut feeling that they were created from when I access my Ubuntu partition through Windows. However, there is only one file in each folder called $shtdwn$.req. That isn't a .exe so I want to be sure before I delete. Are all of those folders OK to remove?

---

### Post by wojox on 2009-09-12
You can remove them. See here. Similar problem:

[http://ubuntuforums.org/showthread.php?p=7376041](http://ubuntuforums.org/showthread.php?p=7376041)

---

### Post by itsjareds on 2009-09-12
Thanks. Everything looks clear now.

---

