---
title: "how to execute 'fortune | cowsay' when the terminal is opened?"
date: 2011-06-18
forum: General Help
---

### Post by rockager on 2011-06-18
i decided to spice up my terminal, so i've installed the cowsay and fortune packages. i want the terminal to display the cow and the quote when i open my terminal.
how do i do it??

---

### Post by Lars Noodén on 2011-06-18
Put it in ~/.bashrc and it will get executed anytime you enter the shell.

---

### Post by amauk on 2011-06-18
edit ~/.bashrc
and add at the bottom
```
/usr/games/fortune | /usr/games/cowsay
```

---

### Post by Elfy on 2011-06-18
Add it to your bashrc.

For example adding 

```
cowsay -f tux 'JOIN US!!!'
fortune 
```

to the end of .bashrc gives this 

```
 ____________
< JOIN US!!! >
 ------------
   \
    \
        .--.
       |o_o |
       |:_/ |
      //   \ \
     (|     | )
    /'\_   _/`\
    \___)=(___/

A banker is a fellow who lends you his umbrella when the sun is shining
and wants it back the minute it begins to rain.
		-- Mark Twain
hobgoblin@hobgoblin:~$ 
```

---

### Post by rockager on 2011-06-18
thanks a lot Lars, amauk and forestpiskie :)

---

