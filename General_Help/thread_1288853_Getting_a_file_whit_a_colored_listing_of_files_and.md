---
title: "Getting a file whit a colored listing of files and dir's like 'ls' in 'tty'"
date: 2009-10-11
forum: General Help
---

### Post by of_darkness on 2009-10-11
Is there any program or script that can do this?
 
 What I'm looking for is getting a file whit the colouring and look of the output that ls produces in a terminal.

---

### Post by eric3_14159 on 2009-11-09
Well, you can call ls with the argument "--color=always" included, which will make it print out the color-causing escape sequences even if you, say, redirect the output to a file with >

The problem is that these escape sequences are unusual characters. If you view the file in the terminal, with cat for example, then you will see the colors as if it were from a normal ls. However, actually looking at the file, in a text editor, will show various unusual characters, including some unprintable ones like ASCII 27 (Escape). Making use of this is difficult.

If you wanted, you could probably write a script which would convert the escape sequences to color information another program could interpret, such as HTML.

The full-color output of ls has this form for a given file "filename.dat", where ^[ represents ASCII character 27, NN is the foreground character code, and MM is the background character code:
^[[NN;MMmfilename.dat^[[00m

It also looks like the file begins with an extra ^[[00m

Oh, and if the file is just printed normally, then NN;MM is simplified to "00".

If you really want to use this, then you'll have to write a pattern matcher, look up the color codes for your particular terminal, and have it convert each file to, for example, some form of '<div style="color: NN; background: MM">filename.dat</div>' line.

---

