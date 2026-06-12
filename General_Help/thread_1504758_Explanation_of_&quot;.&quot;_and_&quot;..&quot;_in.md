---
title: "Explanation of &quot;.&quot; and &quot;..&quot; in directories?"
date: 2010-06-08
forum: General Help
---

### Post by rbc on 2010-06-08
If I open terminal and type ls –a, the first directories listed are:
.
..

I understand their functions, I think, in that the double dot is a “path” to the parent directory, and the single dot is a “path” to the current directory, but why are they there? What is the purpose in having a “path” to a directory that you are already in? There was a recent article in Linux Journal or Linux Mag, but I did not bookmark it and doing a google search for a “dot” does not yield much that is useful, so I’d be grateful if anyone could provide a link or an explanation.

---

### Post by _khAttAm_ on 2010-06-08
I think you are looking for this: [http://www.linux-mag.com/cache/7735/1.html](http://www.linux-mag.com/cache/7735/1.html)

---

### Post by jerome1232 on 2010-06-08
.. is a link to the parent directory, it's useful if you need to go a directory up but don't necessarily know what the parent directories name is.

ie

I want a file that I know is one directory up from my pwd and in a Pictures folder. The following command will get me there.

```
cd ../Pictures
```

I rarely use the ., only when I need to execute a script in the current directory and I don't want the path searched.

```
./script.sh
```

I'm sure someone can offer much better usage examples than I can however. :P

---

### Post by jrg3 on 2010-06-08
Single dot is extremely useful in scripts. It allows the script to reference the "here" point wherever "here" may be.

---

### Post by rbc on 2010-06-08
_khAttAm_,
That is exactly the article I was referring to. Thank you. It is now bookmarked.

jerome1232 and jrg3,
Thank you also. I have done very little script writing. I assumed the “dot” in ./script.sh was somehow needed because it was a script, as opposed to some other type of file. So “./script” is actually the same as typing “CurrentDirectory/script.sh”?

---

### Post by rbc on 2010-06-08
```
So “./script” is actually the same as typing “CurrentDirectory/script.sh”? 
```

Scratch that. That was a stupid question, or at least a poorly worded one. I think i get the gist of it now. Thank you

---

