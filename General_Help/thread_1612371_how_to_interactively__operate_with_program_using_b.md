---
title: "how to interactively  operate with program using bash"
date: 2010-11-03
forum: General Help
---

### Post by richard_wu0313 on 2010-11-03
how to interactively operate with program using bash?
such as program would ask user to select choice between "a/b/c" and then input enter to confirm?
i know i could use 
program << EOF 
a
EOF  

 to choise "a", but how to input "enter", so that i could call this program in my script.

---

### Post by TSJason on 2010-11-03
richard,

Use the "read" command. Like:

```

echo 'Would you prefer a, b or c?'
read answer

```

Their choice is now recorded in variable $answer

---

### Post by richard_wu0313 on 2010-11-04
yes, i know what u mean, read is used to accept user input and store the input value to some variable, however, what i want is some command that could send "enter" to program if the program need input "enter". i know what i want input into program, so i don't care whether to store in a variable.

---

### Post by Crusty Old Fart on 2010-11-04
Have you tried Whiptail?
whiptail - display dialog boxes from shell scripts
```

man whiptail

```

---

### Post by TSJason on 2010-11-04
expect:
[http://myithaca.wordpress.com/2009/06/21/expect-scripting-tutorial/](http://myithaca.wordpress.com/2009/06/21/expect-scripting-tutorial/)

---

### Post by Crusty Old Fart on 2010-11-04
[SIZE=1]**[COLOR=Red]Ooops...I blew it![/COLOR]**[/SIZE]

I should have read Richard's question more carefully.

Jason nailed it by suggesting: expect

To send "enter" (aka carriage return) you can do it with the following expect command:
```

send " \r"
[br]1[/br]
[COLOR=Blue]***(Note: The blank space between the first double quote and the backslash is intentional.)***[/COLOR]

```Incidentally, whiptail comes pre-bundled with Lucid. Expect can be installed from Ubuntu Software Center.

Hats off to Jason. Good call.

Crusty

---

