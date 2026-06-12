---
title: "Is there is any application to join files downloaded from rapidshare??"
date: 2010-05-30
forum: General Help
---

### Post by Dallas.Dude on 2010-05-30
[B]Is there is any application to join files downloaded from rapidshare??

[/B]Generally i use hjsplit to join these files in windows.. 
what application i have to use to join those files in ubuntu.
They have an extension like 001,002,etc...
Please help.

Thanks
:guitar:

---

### Post by confused57 on 2010-05-30
Install wine from the Ubuntu repository, then download & install the HJSplit .exe for Windows.
Even Quickpar .exe should work with wine.

---

### Post by frt975 on 2010-05-30
I'm not sure about this but put them all in the same dictionary and open the first.

---

### Post by Dallas.Dude on 2010-05-31
I will try and let u know..

---

### Post by sdennie on 2010-05-31
If they are numbered sequentially and the only files in a directory, you might try something like:

```

cat * >> ../output_file

```

---

### Post by fooman on 2010-05-31
there is a version of hjsplit that works with linux:

[http://ubuntuforums.org/showpost.php?p=7909007&postcount=15](http://ubuntuforums.org/showpost.php?p=7909007&postcount=15)

as it says in that post....you will need to have java runtime installed.

---

### Post by sarin_cv on 2010-05-31
are u talking about the rar files with extensions r01, r02 etc? If yes, you can use the ubuntu utility itself provided 'rar' must be installed. Just right click on the first file and select extract here...

---

### Post by satish_j on 2010-05-31
Open terminal
cd to directory containing 001,002,...00n files and run
```

cat filename.001 filename.002..........filename.00n > whateverfilename.extension

```
Note:'extension' above is the extension of the final file..eg:rar,avi,mkv,..etc

---

### Post by shai3421 on 2010-05-31
> **sarin_cv said:**
> are u talking about the rar files with extensions r01, r02 etc? If yes, you can use the ubuntu utility itself provided 'rar' must be installed. Just right click on the first file and select extract here...

I agree. Those are just rar files, even with the extension *.001, *.002, etc.. any archiver that can extract rar files should be able to extract those once you put them all in the same directory and tell it to extract the first one (eg *.rar).

---

### Post by Mark Phelps on 2010-05-31
> **shai3421 said:**
> I agree. Those are just rar files, even with the extension *.001, *.002, etc.. any archiver that can extract rar files should be able to extract those once you put them all in the same directory and tell it to extract the first one (eg *.rar).

Not true -- at least, not always.

Sometimes, they ARE RAR files, but most often, they are pieces of a file -- and while they CAN be joined with a filesystem command, HJSplit (for which someone already mentioned there is a JAR version that runs in Linux) is the easier way to do it.

---

### Post by lavinog on 2010-05-31
> **Mark Phelps said:**
> 
Sometimes, they ARE RAR files, but most often, they are pieces of a file -- and while they CAN be joined with a filesystem command, HJSplit (for which someone already mentioned there is a JAR version that runs in Linux) is the easier way to do it.
What is wrong with the cat command that was mentioned a couple of times before.

---

