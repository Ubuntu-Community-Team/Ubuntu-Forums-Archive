---
title: "Terminal command."
date: 2009-08-10
forum: General Help
---

### Post by Chamillionaire2 on 2009-08-10
What's Up?

Would You believe it? I'm stuck with another problem, With the latest advancement on my project, Cometh the error's. So with some help from some very nice Ubuntu forum user's code we can search through files for links and save them into a alternative file via terminal [or executable text file]

```
grep "http://" Input.txt | sed 's/^.*http:/http:/' | sed 's/\s.*$//' | sort >> Output.txt
```

Now Here comes the twist, in the document's its going to be searching which are quite big, the links i want are always after the html code <b> _Example: <b>[http://ubuntuforums.org/](http://ubuntuforums.org/)_ their are other links but their not the ones i want.

i did try ```
grep "<b>http://" Input.txt | sed 's/^.*http:/http:/' | sed 's/\s.*$//' | sort >> Output.txt
```

Which gets the links fine, But the Output file is still very large.
But here cometh the other problem, Since the files are very large, SED seems to have a hard time changing the text <b>, On-top of that it has to perform other duty's as well. 

I left it for about 15 mins but when i came back SED was still running and using alot of CPU, i had to kill the process. So my question is how do i troll thourgh files replacing any <b> text with nothing without taking up too much CPU?

Thanks Bye.

---

### Post by Chamillionaire2 on 2009-08-10
[COLOR="White"]g[/COLOR]

---

### Post by Chamillionaire2 on 2009-08-10
[COLOR="White"]Last Bump.[/COLOR]

---

### Post by unutbu on 2009-08-10
Could you post a snippet of your Input.txt and what you'd like the corresponding Output.txt to look like?

---

