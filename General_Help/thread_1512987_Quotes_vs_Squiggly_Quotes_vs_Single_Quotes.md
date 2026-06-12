---
title: "Quotes vs Squiggly Quotes vs Single Quotes"
date: 2010-06-18
forum: General Help
---

### Post by COKEDUDE on 2010-06-18
Could someone please explain the difference between Quotes vs Squiggly Quotes vs Single Quotes. When I did these commands only the first one worked correctly. Also do I need to use quotes since I'm only searching for one word?
sudo grep -R "MARS" /etc/*
sudo grep -r “MARS” /etc*
sudo grep -r “MARS” /etc/*
sudo grep -R “MARS” /etc/*

I was reading this about how search for text in files.
[http://www.cyberciti.biz/faq/howto-search-find-file-for-text-string/](http://www.cyberciti.biz/faq/howto-search-find-file-for-text-string/)
[http://www.cyberciti.biz/faq/howto-use-grep-command-in-linux-unix/](http://www.cyberciti.biz/faq/howto-use-grep-command-in-linux-unix/)
[http://www.iceteks.com/articles.php/grep/1](http://www.iceteks.com/articles.php/grep/1)

---

### Post by J V on 2010-06-18
You only need the word if it's just one word you are looking for.

As for the quotes, it looks like you have "Fancy" quotes on your keyboard.

Normal ASCII quotes have a low value, your quotes have a high value. In essence, the opening and closing quotes are completely different characters.

Single (') and double (") *straight* quotes should work fine.

---

### Post by COKEDUDE on 2010-06-19
> **J V said:**
> You only need the word if it's just one word you are looking for.

As for the quotes, it looks like you have "Fancy" quotes on your keyboard.

Normal ASCII quotes have a low value, your quotes have a high value. In essence, the opening and closing quotes are completely different characters.

**Single (') and double (") *straight* quotes should work fine.** 

Whats the difference between Single and double straight quotes?

---

### Post by jerome1232 on 2010-06-19
Mostly nothing.


except you can't do this

'I can't quote this string' 

but you can do this

"I can't quote this string" 

where as you can't do this

"Jill said, "Hey!", as she walked"

where as you can do this

'Jill said, "Hey!", as she walked'

You can use an escape character if you  need to use double quotes inside a quoted string though.

ie, (at least I believe that would work)

"Jill said, \"Hey!\", as she walked"


I believe some programing languages treat '' strings different than "" strings.

---

### Post by COKEDUDE on 2010-06-22
Here's what happened when I popped it in the terminal. 
```
~ $ echo "Jill said, \"Hey!\", as she walked"
bash: !\",: event not found
~ $ echo 'Jill said, "Hey!", as she walked"
> 'Jill said, "Hey!", as she walked"
> 'Jill said, "Hey!", as she walked"
Jill said, "Hey!", as she walked"
Jill said, Hey!, as she walked
'Jill said, Hey!, as she walked

```

---

