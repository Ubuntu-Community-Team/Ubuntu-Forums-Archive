---
title: "using grep awk or any other unix tool to rearrange a file"
date: 2012-08-21
forum: General Help
---

### Post by sd@ksu on 2012-08-21
I have a file where I have a few lines like below:
> 
#S **_[COLOR="Red"]1[/COLOR]_** **_[COLOR="red"]some-test[/COLOR]_**  
#D some-test  
#M some-test  
#X **_[COLOR="red"]10[/COLOR]_** Steps ( **_[COLOR="red"]20[/COLOR]_**)
#N 4
#L A B C
1 2 3
4 5 6
7 8 9
#R **_[COLOR="red"]17 11 12[/COLOR]_**

#S 2 some-test  
#D some-test  
#M some-test  
#X 30 Steps ( 30)
#N 4
#L A B C
1 2 3
4 5 6
7 8 9
#R 10 11 12

#S 3 some-test  
#D some-test  
#M some-test  
#X 30 Steps ( 30)
#N 4
#L A B C
1 2 3
4 5 6
7 8 9
#R 10 11 12

#S 4 some-test  
#D some-test  
#M some-test  
#X 30 Steps ( 30)
#N 4
#L A B C
1 2 3
4 5 6
7 8 9
#R 10 11 12



From the above file, for each section marked by "#S", I want to save the number/texts marked as bold+underline+RED in color into one line as below:
[HTML]
#S 1 10 20 17 11 12 some text
#S 2 ... like this
[/HTML]

I can use grep and awk to take out texts from a single line but I do not know how to put texts from a line below into same file in destination: i.e., I do not know how to put the texts in line starting with "#S" and "#X" in one single line in output file. ALso, there is no space between the ending of the number in bracket and the closing bracket, e.g., "[COLOR="Red"]( 20)[/COLOR] in #S 1" .PLease help.

---

### Post by sanderj on 2012-08-22
No grep needed; just awk. Pseudo-code:


/#S/ { put info into variable-S }
...
/#R/ { print everything, plus info this line }

---

### Post by Vaphell on 2012-08-22
```
$ awk '/^#S/ { s1=$2; gsub("^"$1" "$2" ", "", $0); s2=$0; }
       /^#X/ { x1=$2; gsub("[()]","", $NF); x2=$NF; }
       /^#R/ { gsub("^"$1" ", "", $0); print "#S", s1, x1, x2, $0, s2; }
      ' in.txt
#S 1 10 20 17 11 12 some-test
#S 2 30 30 10 11 12 some-test
#S 3 30 30 10 11 12 some-test
#S 4 30 30 10 11 12 some-test

```

---

### Post by sd@ksu on 2012-08-30
Works like a charm..thanks a lot.

---

