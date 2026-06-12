---
title: "gpg limitations"
date: 2012-09-30
forum: General Help
---

### Post by Langstracht on 2012-09-30
I have a number of files that I would like to protect that I (tend to) open simultaneously and I would like to do that (and protect them again) with a single command line instruction like:

gpg -c filename1.ods, filename2.odb, file/...

and thereby only enter 1 passphrase for all of them.  

I couldn't find any information but have been playing around with commas, semi-colons and the like ... and I have come up empty.

I would think it surprising that gpg doesn't support what I am trying to do but, in the lack of any information, who knows.

Can anyone help?

TIA

---

### Post by cprofitt on 2012-09-30
I believe you have to use one of the following:  

> gpg --decrypt --multifile

or

> gpg --decrypt-files

---

### Post by Langstracht on 2012-09-30
Thanks for your reply.

You may be right about the commands you offer ... but I guess I haven't quite known what to do with them.  I've tried adding a list of files with spaces, commas with and without spaces, semi-colons likewise, as well as leaving out "-multifile and -files and I can't get anything to work.

If those commands could be confirmed complete with the syntax of adding the file names (which I am assuming is necessary) that would be VERY helpful.

And of course there's always how to encrypt.  Or are you saying they have to be done individually?

Thanks again.

---

### Post by SideShowFry on 2012-10-02
I recently succeeded in doing something similar to decrypt, piping the filenames in via STDIN:

```
ls *.gpg | gpg --multifile --decrypt
```


All files had been encrypted with the same symmetric passphrase.  I was prompted once for the passphrase, and all the files were decrypted using their original filenames (even though the gpg man page says --decrypt "never writes to the  filename  which is included in the file").

---

### Post by SideShowFry on 2012-10-02
> **SideShowFry said:**
> all the files were decrypted using their original filenames (even though the gpg man page says --decrypt "never writes to the  filename  which is included in the file").

Seems to be using the current filename of the .gpg file, not necessarily the original filename, for the output filename.

So:

encrypting 123.txt to 123.txt.gpg
then renaming the result to abc.txt.gpg
then decrypting

results in abc.txt

---

### Post by Langstracht on 2012-10-02
Well that certainly works!  Thank you for that!!!

How about encrypting though -  changing decrypt to encrypt does NOT do it.

It'd sure be nice to be able to encrypt then in the same way.

But, again, many thanks.

---

### Post by SideShowFry on 2012-10-02
Ok, so, -c and -encrypt encrypt differently.  Assuming you want to use -c, as per your first post, then -multifile isn't available.

You could do a shell script that prompts for the passphrase, perhaps like this untested code:

```

set +x  #hides the password from screen

PWD1hash=14758f1afd44c09b7992073ccf00b43d
PWD2=foo
PWD2hash=bar

until [[ "$PWD2hash" && "$PWD1hash  -" = "$PWD2hash" ]]; do
	read -s -p "Enter passphrase:" PWD2; echo;
	PWD2hash=`echo $PWD2 | md5sum -`
done

```

then iterate over your list of files (generate the list with ls, or keep it in a file, or whatever), something like:

```

set +x
gpg  -o "$x.gpg" --passphrase $PWD2 -c "x" 

```


Or, maybe you should just tar the files together, and run gpg on just that .tar file.  Or just put all the files in an AES256 encrypted 7zip file.

---

### Post by SideShowFry on 2012-10-03
Oh, yeah, another thing: if you're opening and changing these files, and you're doing so with LibreOffice, maybe just use the LibreOffice encryption.  I've read that it's good, and it would save you a few steps.

---

### Post by Langstracht on 2012-10-03
Actually the neanderthal in me uses .txt files whenever I can.  I don't think any of the editors support encryption.  But I could very well be wrong.

That said thanks so much for the script.  I'll see what I can do with it.

---

### Post by SideShowFry on 2012-10-03
Yeah, if it were encrypted, it wouldn't really be a .txt file anymore.  

The script path is definitely workable, but, you could probably come up with a one line tar | gpg or 7zip solution.

---

