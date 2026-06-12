---
title: "Bash script - Center text on screen"
date: 2012-07-17
forum: General Help
---

### Post by gacanepa on 2012-07-17
Hi all,
I would like to know if it is possible to center some text on the screen using a bash script.
Example:
```
#!/bin/bash
echo "Centered text"
```
I can add spaces before and after the text string to try to manually center it (but this would sort of work only for a certain screen resolution), but it won't look as good as if there is something that can be inserted in the code that will work with all screen resolutions.
Suggestions are welcome! Thanks in advance.

---

### Post by Vaphell on 2012-07-17
custom function
```
echo_c()
{
  w=$(stty size | cut -d" " -f2)       # width of the terminal
  l=${#1}                              # length of the string
  printf "%"$((l+(w-l)/2))"s\n" "$1"   # print string padded to proper width (%**W**s)
}
```
test
```

$ text="(centered text)" 
$ echo_c "$text"
                       (centered text)                        [COLOR="Blue"]|[/COLOR]
$ echo_c "$text$text$text"                                    
        (centered text)(centered text)(centered text)         [COLOR="Blue"]|[/COLOR]
$ echo_c "$text$text"
                (centered text)(centered text)                [COLOR="Blue"]|[/COLOR]
```
it won't work correctly in case of l>w - keep that in mind or add some additional logic supporting such cases.

---

