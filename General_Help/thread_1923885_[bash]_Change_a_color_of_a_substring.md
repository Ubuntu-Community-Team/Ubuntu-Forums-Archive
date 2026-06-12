---
title: "[bash] Change a color of a substring"
date: 2012-02-11
forum: General Help
---

### Post by xqwzts on 2012-02-11
Hello!

I need to write a script in bash for my university classes, and I came up with an idea of a program that would test the speed of typing - there is some random text, and the script measures time, number of errors etc. The text would be visible on the screen all the time, and I would like to dynamically refresh it and change the color of correctly written characters to green (or to red - for those which are wrong). This would require some way of manipulating a color of a single character in a string - is something like that even possible? 

I will be very grateful for any suggestions.
PS. Sorry for my English, if there are any mistakes.

---

### Post by Paddy Landau on 2012-02-12
What are you using to display the text?

If it is within the terminal, learn about [ANSI escape codes]("http://en.wikipedia.org/wiki/ANSI_escape_code"). For example:
```
$ echo -e 'See my \e[31mred\e[0m text.'
See my [COLOR=Red]red[/COLOR] text.
```If you want a GUI from Bash, I recommend looking at [yad]("http://code.google.com/p/yad/") ([installation instructions]("http://www.webupd8.org/2010/12/yad-zenity-on-steroids-display.html")).

Ideally, you'd want to write it in a programming language such as Python, C++ or whatever.

---

