---
title: "[Needed]Winrar Commnand"
date: 2010-02-15
forum: General Help
---

### Post by CatchItBaby on 2010-02-15
I was extraction some file through command line then i encounter on notification from winrar

[IMG]http://i49.tinypic.com/v4z7u8.jpg[/IMG]

This file exist what u want to do 
replace
never
quite


I don't want that winrar will prompt me to choose action.

Everytime whenever this situation occur it will overwrite / skip that file 

Syntax i m using for unrar

rar e -pmypassword filename

Plz suggest me appropriate solution

Thanks


Edit : [Question is Updated]("http://ubuntuforums.org/showpost.php?p=8858659&postcount=7")

---

### Post by zvacet on 2010-02-16
Read [this.]("https://help.ubuntu.com/community/FileCompression#Rar (.rar)")

---

### Post by CatchItBaby on 2010-02-16
U didn't get my quesiton plz read it again...

---

### Post by CatchItBaby on 2010-02-17
Any one ?

---

### Post by howefield on 2010-02-18
Open a terminal and type man rar

All the options and switches are detailed in there.

Sounds like you need -o+

PS. rar is  not winrar.

---

### Post by CatchItBaby on 2010-02-21
Thanks :) :popcorn:

---

### Post by CatchItBaby on 2010-02-21
I hv one more question

Suppose i hv These rar files..and files are Password protected

movie1.part1.rar
movie1.part2.rar
movie1.part3.rar
movie1.part4.rar

Password : ubuntu.com

game1.part1.rar
game1.part2.rar
game1.part3.rar
game1.part4.rar

Pass : No password

Syntax i m using : rar e -o- -pubuntu.com

Quesiton is that

- > I want to delete rar files which are succesfully Extracted and it will delete sucessfully rar files .. if rar file got any error like ... Wrong password , crc error then it will not delete rar files...

- > suppose password is wrong then the movie1.part1.rar... and so on got wrong password error then it will not delete those rar files and game1.part1.rar... and so on will be extracted succesfully then it will delete those rar files and also deleted there sub rar parts too like . part1.rar , part2.rar

I hope You will guide me i right Ways

Thnx for reading :)

---

### Post by howefield on 2010-02-21
> **CatchItBaby said:**
> Thnx for reading :)

You're welcome but you seem to be making a number of statements rather than asking a question, can you re phrase and ask again.

I'm not sure what you want as an end result.

---

### Post by CatchItBaby on 2010-02-21
I want that it will delete those files which are successfully extracted..

If any file got any error like wrong passwrod , crc error then it will not delete those rar file only

---

