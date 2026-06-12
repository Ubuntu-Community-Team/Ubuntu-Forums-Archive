---
title: "best way to compress and encrypt large files?"
date: 2012-04-13
forum: General Help
---

### Post by sohlinux on 2012-04-13
Hello,

What is the best way to compress and encrypt large files over 100gb? I cannot use password protected zip files because they dont allow over 4gb in size.

I am looking for something that will compress and encrypt at the same time and when I come to extract the files I simply enter the password and extract them.

thanks

---

### Post by sohlinux on 2012-04-13
anyone? :p

---

### Post by jjpcexpert on 2012-04-13
I don't know what encryption method allows you to encrypt and compress, but compress using Gzip, and then use something strong, like AES.

---

### Post by Fwission on 2012-04-13
Is the compression part really that important, I find most of the time compression doesn't even do that much

---

### Post by sohlinux on 2012-04-13
I need to compress the files because they are going onto a cloud/backup.

When I compress the files it takes many hours because the backup.tgz files are 100GB, then after compressing them I have to encrypt them which also takes many hours so I really need a solution which is capable of compressing and encrypting at the same time.

I think maybe zip64 is capable but I cannot find any info on installing and using it on linux.

thanks

---

### Post by sohlinux on 2012-04-14
I managed to do what I wanted using rar and unrar

to compress and password protect a directory using rar
```

rar a -m5 -R -ppassword /path/_to_output.rar /path/to_the_directory_you_want_to_compress

```


to extract a single rar file to a directory with the same name as the rar file (in the current directory)
```

unrar x output.rar

```


to extract all rar files to separate directories (in the current directory)
```

find -type f -name '*.rar' -exec unrar x {} \;

```

---

