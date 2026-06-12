---
title: "Search text string in multiple PDF files using the terminal"
date: 2011-03-04
forum: General Help
---

### Post by orodoni_le on 2011-03-04
I have multiple PDF file in a series of folder, mostly scientific articles. In the past, under Windows, I used Google Desktop to search for an specific text string on those documents. Now, I managed to look search an specific text string in all PDF documents under a certain folder using a combination of **grep** and **pdftotext** (the later included with the package **poppler-tools**)

If I type under a certain folder:
```
find . -name '*.pdf' | xargs -ifoo sh -c 'echo "\033[34;1m// === PDF Document:\033[33;1m $foo\033[0m" ; pdftotext -enc Latin1 "foo" - | grep -i --color=always "String.To.Find"'
```
It will convert all the pdf files to text (handling the ligatures created by LaTeX with the -enc Latin1 option), and will search for the "String.To.Find" in these documents, without paying attention to the character cases, printing the output into the console with nice colors. The points to separate words are the only way I found to handle spaces.

However, as I use this option quite frequently, I want to create a bash function and include it in my ~/.bashrc file. I tried this
```
function findpdfs() {
find . -name '*.pdf' | xargs -ifoo sh -c 'echo "\033[34;1m// === PDF Document:\033[33;1m $foo\033[0m" ; pdftotext -enc Latin1 "foo" - | grep -i --color=always $1'
}

```
After putting that in my ~/.bashrc file, I tried to execute
```
findpdfs "String.To.Find"
```
but it gives an error during the grep for each pdf file under that folder
```
// === PDF Document: $./filename.pdf
Usage: grep [OPTION]... PATTERN [FILE]...
Try `grep --help' for more information.
```
I think that the problem is that, after three pipes |, the **grep** command doesn't recognize the argument to the bash function (**$1**). Any ideas about how to solve this issue?

---

### Post by orodoni_le on 2011-03-05
What I've done so far is include this function to ~/.bashrc, which uses a recursion instead of find and pipes to look for the PDF documents
```
function findpdfs() {
for i in *.pdf
  do
  echo -e "\033[34;1m// === PDF Document:\033[33;1m $i\033[0m"
  pdftotext -enc Latin1 "$i" - | grep --color=always -i $1
done
}

```
It works. The only issue is that it doesn't look for PDF files in the subfolders.
Anybody knows how to modify the function in the previous post to recognize the argument, or how to modify the line
[INDENT]"[FONT="Courier New"]for i in *.pdf[/FONT]"[/INDENT]
so it will look for PDF files in the subfolders?

---

### Post by AlphaLexman on 2011-03-05
> **orodoni_le said:**
> how to modify the line
[INDENT]"[FONT="Courier New"]for i in *.pdf[/FONT]"[/INDENT]
so it will look for PDF files in the subfolders?
```
for i in $(find . -name "*.pdf")
```

---

### Post by orodoni_le on 2011-03-05
> **AlphaLexman said:**
> ```
for i in $(find . -name "*.pdf")
```

Thanks, it works. Now I have
```
function findpdfs()
{
for i in $(find . -iname '*.pdf')
  do
  echo -e "\033[34;1m// === PDF Document:\033[33;1m $i\033[0m"
  pdftotext -enc Latin1 "$i" - | grep --color=always -i $1
done
}
```
The -iname option is to include the *.pdf and *.PDF. However, the command
```
findpdfs "string.to.search"
```
still gives an error with filenames that contains spaces. Any further advice?

---

### Post by SeijiSensei on 2011-03-05
ignore

---

### Post by orodoni_le on 2011-03-05
I found two solutions

[SIZE="3"]**1. Change $IFS variable**[/SIZE]
I don't like this solution, because I think that a crash during my script will cause that the $IFS variable (containing an space by default), will stay changed forever and crash something else in the future
```
function findpdfs() {
SAVEIFS=$IFS
IFS=$(echo -en "\n\b")
for filename in $(find . -iname '*.pdf')
do
  echo -e "\033[34;1m// === PDF Document:\033[33;1m $filename\033[0m"
  pdftotext -enc Latin1 "$filename" - | grep --color=always -i $1
done
IFS=$SAVEIFS
}
```
I don't know how to limit this IFS change only to this bash script. My preferred solution is the number 2.

[SIZE="3"]**2. Use [FONT="Courier New"]while read[/FONT] instead of [FONT="Courier New"]for[/FONT]**[/SIZE]

```
function findpdfs() {
find . -iname '*.pdf' | while read filename
do
  echo -e "\033[34;1m// === PDF Document:\033[33;1m $filename\033[0m"
  pdftotext -enc Latin1 "$filename" - | grep --color=always -i $1
done
}

```
Works perfectly.:D Thanks!!

---

### Post by thewanderorux on 2012-11-28
[SIZE=3][B]This is a great way to search in multiple pdfs[SIZE=3], thank you all!!
[/SIZE][/B][/SIZE]I was looking for indexing multiple pdf files and searching in them, but your solution to this is way more cool!

Let me summarize:
1. Put this in ~/.bashrc
```
function findpdfs() {
find . -iname '*.pdf' | while read filename
do
  echo -e "\033[34;1m// === PDF Document:\033[33;1m $filename\033[0m"
  pdftotext -enc Latin1 "$filename" - | grep --color=always -i $1
done
}

```2. restart bash, cd to your pdfs and type
findpdfs "yoursearchtermhere"

I think I'll put this in a nautilus-action and notify-send me the resulting file :)

---

### Post by wildmanne39 on 2012-11-28
Thanks for sharing and please do not post in threads that have not had activity for a year or longer, since this is an old thread it has been closed.

---

