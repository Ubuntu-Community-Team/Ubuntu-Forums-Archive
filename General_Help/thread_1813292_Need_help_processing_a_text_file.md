---
title: "Need help processing a text file"
date: 2011-07-27
forum: General Help
---

### Post by dagoss on 2011-07-27
Hello

I'm having an issue processing a text file on the CLI, and I'm not quite sure what I need to do to solve it.

I have a LaTeX project that I want to convert to epub using pandoc. The latex files are separated such that I have:

main.tex
ch1.tex
ch2.tex
...

In main.tex, there are \input{ch1.tex} (etc) statements to pull in the contents of those files. Unfortunately pandoc doesn't do this and simply prints {ch1.tex} where that file was supposed to be included.

So I need to make a script that searches through main.tex for \input{file} and inserts the contents of file there and removes the input command, then sends the result to pandoc for processing. I don't want it to permanently modify main.tex, through creating a temporary file in the working directory is fine. Something like:

[Find "\input{file.tex}" in main.tex]
[replace "\input{file.tex}" with the contents of file.tex]
[Send result of this process to pandoc -f=latex --smart --standalone INPUT -o main.epub]

---

