---
title: "SED Script"
date: 2009-07-29
forum: General Help
---

### Post by Chamillionaire2 on 2009-07-29
What's Up?

OK, I Want to replace a character with a word i know the command
```
sed s/first/second/ Output.txt >>Finished.txt
```

But Theirs the prob, i dont want to replace a word, the thing i want to replace is a "/" with a word but.

```
sed s///second/ Output.txt >>Finished.txt
```

Wont work lolers. Can anyone suggest a way around this?

Thanks Bye.

---

### Post by sisco311 on 2009-07-29
use the non-quoted backslash (\) escape character:
```
sed "s/\//slash/" file.name >> blah
```

---

### Post by cgb on 2009-07-29
you can use

```
sed s/[/]/second/ Output.txt >>Finished.txt
```

---

### Post by DaithiF on 2009-07-29
yet another way :)
to avoid a visual forest of forward & back slashes, use # character as the sed delimiters and then no escaping of / required

```
sed 's#/#slash#' somefile
```

---

### Post by decoherence on 2009-07-29
```
sed 's#/#slash#' somefile
```

Just so we're clear, you can use any character (as far as I know) as the delimiter, not just "/" and "#". You could use the letter "a" if you wanted but it probably wouldn't be a great idea (particularly in this example)

---

