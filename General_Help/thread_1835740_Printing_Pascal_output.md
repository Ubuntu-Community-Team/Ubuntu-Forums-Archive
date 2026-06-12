---
title: "Printing Pascal output"
date: 2011-08-29
forum: General Help
---

### Post by conradin on 2011-08-29
Hi Everyone!
I am working with a woman who wrote several dozen pascal programs to run in MSDos back around 1990. Last week her windows 1998 laptop died, and she's been having difficulty using DosBox to print. Her programs print no output files, only directly to the screen. Ive tried several MS based solutions but nothing Ive found supports her new USB printer. That said, I think linux might be able to solve this. If I can compile her programs in free Pascal, or gpc, how might I expect to print the screen output?  I wrote a simple hello world type program that writes "Hello world" to the terminal window how could I print that output to one of my networked printers?

Heres my example:
```
program HelloWorld;

begin
  writeln('Hello World');
end.
```
Then at the terminal I compile with gpc pasc7.pas -o hi
and output to the terminal by running the output binary ./hi
 resulting in:
Hello World. Prepare to learn PASCAL!!
 
hiting enter returns my to the $ terminal. 
how would I print that output?

---

### Post by conradin on 2011-08-30
so I figured out printing, I was thinking ./codeHI > lpr but thats wrong its:
```
./codeHI | lpr 
```  that handles simple printing from program piping program output to the printer. though I suspect that her programs may be interactive prior to printing. So Im still not sure how to print whats int the terminal window which has already been processed. I'd like to know if there is any way to do that.

---

