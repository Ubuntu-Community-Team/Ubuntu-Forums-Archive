---
title: "extract text"
date: 2009-11-20
forum: General Help
---

### Post by dragonflyFZX on 2009-11-20
hi, i need help from a linux guru here. I want to extract text from a string. For example:

111éé3'(5555helpYYUNKKKGme009OIIIP

I need a command that counts 8 characters further after finding 'help' and then extracts 2 characters, so the output of this command should be: 'me'.

Can this be done with grep?

Sorry for this simple question
D

---

### Post by lmarmisa on 2009-11-20
May be this is not very smart but it is my proposal:

I suppose that your string is stored in $text

text1=`echo $text | sed 's/.*help........//'`
text2=${text1:0:2}
echo $text2

Best regards,

Luis

---

### Post by dragonflyFZX on 2009-11-20
ok, thanks for the reply, this seems to work, except, the string is long and has 'help' a few times in it. I only need to extract what is 8 characters after the *first* occurrence of 'help'. The method you suggested seems to extract the 'me' that follows 8 characters after the last occurrence of 'help'.

Thanks again

---

### Post by CaKiwi on 2009-11-20
You could use awk. If the text is in file a.dat use
> awk '{if (match($0,/help/)) print substr($0,RSTART+12,2)}' a.dat
If it is in variable $text use
> echo $text | awk '{if (match($0,/help/)) print substr($0,RSTART+12,2)}'

HTH

---

### Post by sisco311 on 2009-11-20
sed:
```
echo "$text" | sed 's/.*help........\(..\).*/\1/'
```

---

