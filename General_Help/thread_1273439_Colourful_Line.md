---
title: "Colourful Line"
date: 2009-09-23
forum: General Help
---

### Post by supravat on 2009-09-23
I am creating a executable file using c in linux...I want to make the output lines colourful...
Example:

main()
{
   printf("Hello");
}

I want to make the "Hello" colourful...How should I do this? Please help me...

---

### Post by The Cog on 2009-09-23
Something line this:
```
red=$'\e[31m'
black=$'\e[0m'
black $red red $black black
```
or in C:
```
printf("\x1b[0mblack \x1b[31mred \x1b[0mblack");
```

google for ansi escape sequences

---

### Post by supravat on 2009-10-03
Thanks...

---

