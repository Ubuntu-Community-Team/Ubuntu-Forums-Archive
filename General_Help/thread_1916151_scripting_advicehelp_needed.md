---
title: "scripting advice/help needed"
date: 2012-01-27
forum: General Help
---

### Post by wayover13 on 2012-01-27
I've tweaked up nano so as to allow me to create nice outlines using this terminal application. You can read about that at [http://audaciousamateur.blogspot.com/2012/01/outlining-with-nano.html](http://audaciousamateur.blogspot.com/2012/01/outlining-with-nano.html) if you're interested.

Next, I tried to figger out a way to make those outlines print nicely on paper. Adding the appropriate TeX mark-up to them, then running pdflatex on them did the trick: got a nice looking, print-ready document like that.

But I still consider this project half finished. See, thus far I've been manually adding the mark-up to the text files. For the project to move to the next level, that mark-up should be added by some program/script.

Essentially what needs to happen is for a few lines of preamble to be added at the beginning of the outline, as well as a few lines appended at the end. Then, additional mark-up needs to be added at each level of the outline. That latter, more complicated task will involve, I presume, regular expression searches and replacements: each new line followed, either by the equals sign, or by some number of spaces and then the equals sign, should replace the equals sign with the mark-up \outl{#} (where # is a number between 1 and 9 depending the presence or absence, as well as number of, spaces, between the new line and the equals sign). A more detailed explanation can be found at
[http://audaciousamateur.blogspot.com/2012/01/addendum-to-second-installment-texlatex.html](http://audaciousamateur.blogspot.com/2012/01/addendum-to-second-installment-texlatex.html)

I'm at sort of a loss for where even to start looking for a solution to the processing I want to happen with these outline files. I do fine with editing configuration files so as to implement limited customizations of programs like nano. And I've even created some extremely rudimentary bash scripts in my time. But I'm finding myself a bit lost as to where even to begin searching for a solution to the file processing task I've discussed here.

It seems tools like awk and sed, for example, might be relavent. But looking over their man pages I get lost almost immediately: they start throwing around concepts and terminology with which I am unfamilar right off the bat. I end up not even being sure that they are applicable to this task.

Then again, I understand python or perl scripts could help as well. But I know almost zilch about those languages (actually, I did once get as far as creating hello.py). So I need some suggestions even to get started.

What are some of the ways of skinning this cat? Can a bash script do this sort of thing? Anyone up for making a mock-up python or perl script that a rank newbie such as meself might be able to grok and tweak? Halp!

TIA,
James

---

### Post by Cookieh on 2012-01-27
Try to follow this guide on PDF:
[http://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&ved=0CCUQFjAA&url=http%3A%2F%2Ftldp.org%2FLDP%2Fabs%2Fabs-guide.pdf&ei=Ye4iT6jbB-jC0QWAv8XPCg&usg=AFQjCNEw8yUWMbJEjjX4zsRQqd5Nyehp6Q&sig2=hs3m9OAqjl0oV-_fUSyiUQ](http://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&ved=0CCUQFjAA&url=http%3A%2F%2Ftldp.org%2FLDP%2Fabs%2Fabs-guide.pdf&ei=Ye4iT6jbB-jC0QWAv8XPCg&usg=AFQjCNEw8yUWMbJEjjX4zsRQqd5Nyehp6Q&sig2=hs3m9OAqjl0oV-_fUSyiUQ)

It has helped me quite a lot, hope it helps you too...

---

### Post by wayover13 on 2012-01-27
Yeah, I actually ran across that in my searches. I wasn't sure it would be applicable to me since, in order to undertake advanced bash scripting, it seems one should be proficient at basic bash scripting--which I'm not. That point aside, though, does this mean you think that a bash script could accomplish the task I've described? I.e., it could search and replace regular expressions inside a file?

James

---

### Post by wayover13 on 2012-01-28
Looking over the ABS document I came across the following: [http://www.tldp.org/LDP/abs/html/contributed-scripts.html#TOHTML](http://www.tldp.org/LDP/abs/html/contributed-scripts.html#TOHTML) . That's a bash script that converts a text file to html--something very close to what I need to do. Both my project and the html conversion involve prepending and appending lines to the text file, and both involve inserting some mark-up into the text file. The script uses sed to find places where mark-up is to be  inserted, but my file may not require that since my tags only need to be inserted in a certain relation to some new lines, not in the midst of lines or paragraphs. Anyway, I just want to ask whether someone who knows bash scripting and who might read this could weigh in as to whether they agree that this bash script could be adaptable to the processing scenario I've outlined above.

Thanks,
James

---

