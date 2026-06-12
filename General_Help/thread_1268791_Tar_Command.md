---
title: "Tar Command"
date: 2009-09-17
forum: General Help
---

### Post by ChrisB111 on 2009-09-17
I would like to unpack all the .tgz archives in one directory in to a another specified sub directory, I have no bash experience, and so far I have worked out I need to use the tar command, and the -C parameter to specify the directory but I just get the a:
```
tar: -C=/home/chris/tartest/sub/: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now

``` error using this command:
```
tar -xvvxf -C=/home/chris/tartest/sub/ *.tar.gz
```
I am using tar.gz archives to test my command and the /home/chris/tartest/sub/ as the sub directory I want the extracted file in for this test, I am executing the command in the directory where the archives are. Could someone please tell me where I am going wrong, and if possible how to correct it?

Thanks,

Chris

---

### Post by Penguin Guy on 2009-09-17
Fixed command:
```

for file in *.tar.gz; do echo "Extracting $file:"; tar xvzf "$file" -C "$HOME/tartest/sub/"; done

```


**What it means:**
[PHP]for file in *.tar.gz;     # For each file ending in .tar.gz in the current directory
do
  echo "Extracting $file:";     # Display text: 'Extracting <file>'
  tar xvzf "$file" -C "$HOME/tartest/sub/";     # Untar the file
done[/PHP]


**Untar:**
x - Extract
v - Verbose (display info)
z - Gzip (that's what it's compressed with '.tar.**gz**')
f - Use the file:
C - Extract it to:

---

### Post by ChrisB111 on 2009-09-17
I tried running the command twice but got these errors:
```

chris@chris-desktop:~/tartest$ tar -xvf * -C=~/tartest/sub/
tar: sub: Cannot read: Is a directory
tar: At beginning of tape, quitting now
tar: Error is not recoverable: exiting now
chris@chris-desktop:~/tartest$ tar -xvf *.tar.gz -C=~/tartest/sub/
tar: testa2.tar.gz: Not found in archive
tar: Error exit delayed from previous errors
chris@chris-desktop:~/tartest$ 
```

---

### Post by wojox on 2009-09-17
```
sudo tar -zxvf archive_name.tar.gz -C /tmp/extract_here/
```

---

### Post by Penguin Guy on 2009-09-17
> **ChrisB111 said:**
> I tried running the command twice but got these errors:
```

chris@chris-desktop:~/tartest$ tar -xvf * -C=~/tartest/sub/
tar: sub: Cannot read: Is a directory
tar: At beginning of tape, quitting now
tar: Error is not recoverable: exiting now
chris@chris-desktop:~/tartest$ tar -xvf *.tar.gz -C=~/tartest/sub/
tar: testa2.tar.gz: Not found in archive
tar: Error exit delayed from previous errors
chris@chris-desktop:~/tartest$ 
```
It turns out that tar doesn't support wildcards, try this: [COLOR="Green"]for file in *.tar.gz; do echo "Extracting $file:"; tar xvzf "$file" -C "$HOME/tartest/sub/"; done[/COLOR]
Don't run [the command that wojox posted]("http://ubuntuforums.org/showpost.php?p=7964641"), it won't work and is potentially dangerous.

---

### Post by ChrisB111 on 2009-09-17
Thanks Penguin Guy, that new command works.

Thanks again,

Chris

---

