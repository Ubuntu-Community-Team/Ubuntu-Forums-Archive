---
title: "Batch rtf -&gt; txt with unRTF"
date: 2010-01-26
forum: General Help
---

### Post by sisyphus1978 on 2010-01-26
I want to turn a folder of rtf files <filename.rtf> into filename.txt with unrtf. Any ideas?

for file in *.rtf; do
unrtf --text $file
done

Doesn't seem to work.

---

### Post by t4thfavor on 2010-01-26
Try 

```

for FILE in $(ls|grep *.rtf); do unrtf --text $FILE; done

```

---

### Post by sisyphus1978 on 2010-01-26
That didn't seem to work. 

> Usage: unrtf [--version] [--help] [--nopict|-n] [--html] [--text] [--vt] [--latex] [--ps] [--wpml] [-t html|text|vt|latex|ps|wpml] <filename>


---

### Post by whiskeylover on 2010-01-26
Did you add the "--text" to t4th's code?

---

### Post by t4thfavor on 2010-01-26
You have to add the --text option as I forgot it.

Fixed above.

---

### Post by sisyphus1978 on 2010-01-26
I had added the --text. Mine seems to be a permissions problem. I'm seeing files as green with an asterix (in midnight commander) but I've chmod and chown the folder (and moved it to the home etc). Any ideas?

---

### Post by t4thfavor on 2010-01-26
what does ls -la|grep *.rtf give you?

can you do one manually? as in 

unrtf --text file.rtf 

If so it's not permissions.

---

### Post by sisyphus1978 on 2010-01-26
> what does ls -la|grep *.rtf give you?> can you do one manually? as in  unrtf --text file.rtf Nothing and no. 
Does that mean it's a permissions problem then?

---

### Post by t4thfavor on 2010-01-26
Then your in the wrong directory if there are no RTF's in there, you cannot unrtf them.

This would explain why you can't even do one manually.

you have to cd to the directory

```

cd /path/to/rtf's
/path/to/rtf.shellscript.sh

```


type pwd to see what directory your in, if it's the one with the RTF's in it, then it has to be permissions I guess.

---

### Post by sisyphus1978 on 2010-01-26
I'm not that daft. I was in the correct directory. I will keep working on it...

---

### Post by sisyphus1978 on 2010-01-26
ls -la gives:
> -rwxr-xr-x  1 username username   2308 2009-10-07 16:35 StoryID98741.rtf

ls -la|grep *.rtf does nothing.

---

### Post by whiskeylover on 2010-01-26
Try ls *.rtf instead of piping it to grep.

(I'm not logged in Linux at the moment, so I can't test this.)

---

### Post by sisyphus1978 on 2010-01-26
Yup. I get a list of all the rtf files in the folder.

---

### Post by whiskeylover on 2010-01-26
What does manually running  unrtf --text file.rtf on a file give you?

---

### Post by sisyphus1978 on 2010-01-26
I actually can't get it to work on a single file. However the rtf files were all stored on google docs, so I just redownloaded them all as txt files. Quicker than this way.

Looking at the files in midnight commander they are grey (the new txt files). The rtf files are (as I said) green with an asterisk. I believe this denotes some kind of permissions status (ie protected), though I tried chmod and chown, to no avail.

I'd still like to get this sorted though.

---

### Post by whiskeylover on 2010-01-26
Green most probably means they're marked as executable (see the rwxr-xr-x permissions?) The "x" is for executable.

You can change that using "chmod 644  *.rtf"

---

### Post by sisyphus1978 on 2010-01-26
Shoot. Well that doesn't help then. :)

---

### Post by whiskeylover on 2010-01-26
Although it shouldn't matter even if the files are marked as executable since the program can still read the input rtf files.

---

### Post by sisyphus1978 on 2010-01-26
Okay changed the attribute and no difference. I've tried it on a couple of different RTF files and it looks like it is converting them (the text appears in the terminal) but there is no new text file. And it doesn't look like it's just a text file named rtf (ie the file has formatting).

Is it me?

BTW the man isn't very helpful and neither is --help.

---

### Post by t4thfavor on 2010-01-26
I believe it's my fault, I added the aboe suggestion of ls *.rtf to my script, and it worked fine.


I noted that the script had to be in the directory with all the rtf files as well.

It appeared to work on paper, but I had no RTF's to actually test until now.

```

#!/bin/bash
for FILE in $(ls *.rtf); do 
	unrtf --text $FILE; 
	echo $FILE;
done


```


```

./unrtf.sh 
This is UnRTF, version 0.19.2
By Dave Davey and Marcos Serrou do Amaral
Original Author: Zach T. Smith
Processing Test1.rtf...
### Translation from RTF performed by UnRTF, version 0.19.2
### For information about this marvellous program,
### please go to http://www.gnu.org/software/unrtf/unrtf.html
### document uses ANSI character set
### font table contains 4 fonts total

AUTHOR: chance 
### creaton date: 26 January 2010 14:30 
### revision date: 
### last printed: 
### comments: StarWriter

-----------------
This is an RTF
Blah Blah Blah
Done.
133 words were hashed.
Test1.rtf
This is UnRTF, version 0.19.2
By Dave Davey and Marcos Serrou do Amaral
Original Author: Zach T. Smith
Processing Test2.rtf...
### Translation from RTF performed by UnRTF, version 0.19.2
### For information about this marvellous program,
### please go to http://www.gnu.org/software/unrtf/unrtf.html
### document uses ANSI character set
### font table contains 4 fonts total

AUTHOR: chance 
### creaton date: 26 January 2010 14:30 
### revision date: 
### last printed: 
### comments: StarWriter

-----------------
This is an RTF
Blah Blah Blah
Done.
133 words were hashed.
Test2.rtf
This is UnRTF, version 0.19.2
By Dave Davey and Marcos Serrou do Amaral
Original Author: Zach T. Smith
Processing Test3.rtf...
### Translation from RTF performed by UnRTF, version 0.19.2
### For information about this marvellous program,
### please go to http://www.gnu.org/software/unrtf/unrtf.html
### document uses ANSI character set
### font table contains 4 fonts total

AUTHOR: chance 
### creaton date: 26 January 2010 14:30 
### revision date: 
### last printed: 
### comments: StarWriter

-----------------
This is an RTF
Blah Blah Blah
Done.
133 words were hashed.
Test3.rtf


```

And about not being that daft, you never know. I had to at least make the suggestion.

---

### Post by sisyphus1978 on 2010-01-26
Okay, this is still not working. I put the script in the dir and sh the script: 
> Done.
162 words were hashed.
StoryID95438.rtf
This is UnRTF, version 0.19.2
By Dave Davey and Marcos Serrou do Amaral
Original Author: Zach T. Smith
Processing StoryID95468.rtf...
### Translation from RTF performed by UnRTF, version 0.19.2
### For information about this marvellous program,
### please go to [http://www.gnu.org/software/unrtf/unrtf.html](http://www.gnu.org/software/unrtf/unrtf.html)
### document uses ANSI character set
### font table contains 3 fonts total
### revision date: 7 October 2009 16:35 

-----------------
Done.
320 words were hashed.
StoryID95468.rtf
This is UnRTF, version 0.19.2
By Dave Davey and Marcos Serrou do Amaral
Original Author: Zach T. Smith
Processing StoryID95793.rtf...
### Translation from RTF performed by UnRTF, version 0.19.2
### For information about this marvellous program,
### please go to [http://www.gnu.org/software/unrtf/unrtf.html](http://www.gnu.org/software/unrtf/unrtf.html)
### document uses ANSI character set
### font table contains 3 fonts total
### revision date: 7 October 2009 16:35 

-----------------
But no output files: no txt. There are still only rtf files in the folder. Shouldn't there be the text versions as well?

> And about not being that daft, you never know.
You're right. You never know (and not being able to turn rtf > into txt maybe proves it (me being daft that is).

---

### Post by whiskeylover on 2010-01-26
Here is an example of the usage of unrtf.

[http://pdb.finkproject.org/pdb/package.php/unrtf?rel_id=10.5-i386-0.9.0-bindist](http://pdb.finkproject.org/pdb/package.php/unrtf?rel_id=10.5-i386-0.9.0-bindist)

You need to redirect the output to a new text file. For now, try this code.

```
#!/bin/bash
for FILE in $(ls *.rtf); do 
    unrtf --text $FILE > $FILE.txt; 
    echo $FILE.txt;
done
```
This will create new files with the extension of *.rtf.txt. You can manually rename the files later, or use string functions in bash to get the part before .rtf and then append .txt. 

As I said, I don't have linux right now, so I cannot test.

---

### Post by sisyphus1978 on 2010-01-26
That worked, but all the output files were missing data (ie they were empty but for the unrtf output). I conclude that the files themselves were corrupt in some way. As I already have perfect txt copies I am going to give up and mark this served. I am slowly getting my head around more complex scripting, but it's tough sometimes.

Thanks for helping a guy out.

---

### Post by t4thfavor on 2010-01-26
```

#!/bin/bash
for FILE in $(ls *.rtf); do 
	unrtf --text $FILE|cat >> ${FILE}.txt; 
	echo $FILE;
done


```

The only crappy part is that it outputs a funny header on each file.

Which is fixed by this.
```

#!/bin/bash
for FILE in $(ls *.rtf); do 
	unrtf --text $FILE|cat > ${FILE}.txt; 
	cat ${FILE}.txt|  sed '1,13d' > ${FILE}.txt ;
	echo $FILE;
done

```


For future reference I suppose.

---

### Post by Tee-Bo on 2010-08-29
Hello t4thfavor, 

Thank you for posting this. 

Would you know the syntax to call unrtf from within a Perl program? I am working on a conversion and I have the following challenge: 

I have a .csv file. Some of the fields contain RTF formatted information.  
For each row and for each field in the .csv file I need to: 

- convert the RTF to plain text variable 
- remove any carriage returns within the translated variable
- update the variable  

I have no problem getting the .csv into an array and all. What I am struggling with is the Perl syntax to do something like: 

1) Take this array variable which contains RTF text 
2) urtf it to a variable 

All I have seen so far is methods to apply unrtf to an entire file, not a variable within a program. 

Thank you in advance to anyone who would know! 

TB

---

