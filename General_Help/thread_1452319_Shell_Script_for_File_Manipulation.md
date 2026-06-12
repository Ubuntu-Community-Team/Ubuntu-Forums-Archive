---
title: "Shell Script for File Manipulation"
date: 2010-04-11
forum: General Help
---

### Post by Zerocool3001 on 2010-04-11
I'm trying to write a simple shell script that would organize a list of files in a folder and place files with the same name (but different extensions) into separate folders. I'm used to Java and its been a long time since I wrote anything complicated in a shell script, so I'm pretty rusty. I was wondering if anyone could take a look and tell me the (I'm sure many) things I'm doing wrong? I really appreciate the help.

My intention is to organize a folder of books for import into Calibre. Since Calibre can only tell if two files are different versions of the same book if they are located in a separate folder from the other books, I have to go through the list and:

1. Make a folder for each book, of which exist one or more files
2. Move files with the same name (but different extension) into the folder for that book

I wrote a script to do this, but I was unfamiliar with all the little tricks of bash. For example I was unaware of the built in test statements and of how to use "{}" to parse outputs. Please tell me if I'm close to what I want to do and if theres anything I should correct.

```
#!/bin/bash

books= $(ls);

for x in $books
	do
		CurrentFolder= ${x /.*/};
		if ${x++ /.*/} ==${x /.*/}; then
			mv "$x" "$CurrentFolder";
			x++;
		else
			x++;
			mkdir ${x /.*/};
	done
echo finished;
```


P.S. This is highly embarrassing to post. ;)

---

