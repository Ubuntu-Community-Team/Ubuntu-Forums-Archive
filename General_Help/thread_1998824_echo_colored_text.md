---
title: "echo colored text"
date: 2012-06-07
forum: General Help
---

### Post by Drenriza on 2012-06-07
Hi guys.

How can you in the CLI window, echo colored text? For example red for error and green for "ok".

Kind regards.

---

### Post by Azdour on 2012-06-07
Hi,

Maybe this will help:

[http://tldp.org/LDP/abs/html/colorizing.html](http://tldp.org/LDP/abs/html/colorizing.html)

So to output in green:

```

echo -e "\E[1;32mHello World"

```

The style and colour is defined in the example as: 1;32

0=none, 1=bold, 4=underscore, 5=blink, 7=reverse, 8=concealed

30=black, 31=red, 32=green, 33=yellow, 34=blue, 35=magenta, 36=cyan, 37=white

To reset back to normal text run:

```

tput sgr0

```

---

### Post by Habitual on 2012-06-07
[https://wiki.archlinux.org/index.php/Color_Bash_Prompt#List_of_colors_for_prompt_and_Bash](https://wiki.archlinux.org/index.php/Color_Bash_Prompt#List_of_colors_for_prompt_and_Bash)

---

