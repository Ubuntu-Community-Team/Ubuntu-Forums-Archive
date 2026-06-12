---
title: "SIMPLE small text editor 3 features"
date: 2010-03-07
forum: General Help
---

### Post by kaligus on 2010-03-07
I am looking for an editor to fill a specific request for a mostly non-computer person.  He uses a computer to write manuals and other books for classes he teaches.  He has come to ubuntu so he can more easily access updates, gimp, etc. than he felt he could in Windows.

1)
I need a text editor that can be kept open without bogging things down, or can be loaded fast enough to make him think it is "TSR" (made usable in either case by a keypress on his MS internet antique keyboard)

2)
spell check as you type with editable dictionary (he can add words that will no longer show as incorrect).  Ability to select spelling suggestions easily (left click a misspelled word is his current method).

3)
ability to highlight words that most of us would call syntax highlighting but for words having NOTHING to do with a programming language etc.  I would call it ability to edit the keyword file(s) to make his own languages to be highlighted.

Already rejected:
* anything with millions of complex keys to @#%$^%#$ remember that don't make sense
* gedit
* geany
* kate
* openoffice
* treeline (though he does use it for other things)
* tomboy (the cuss words there are an art form)
* anything emacs/vi or similar (see #1 reject reason at top)
* some gtk-nano clone he has no idea where he found

---

### Post by Kaligo on 2010-03-07
Abiword is supposed to be a simple, lightweight alternative to OO Writer.  Haven't used it in years though, so can't speak of it's current state.

---

### Post by iponeverything on 2010-03-07
Abiword loads pretty quickly.

---

### Post by dcstar on 2010-03-07
Something that does spell checking is not a "Simple Text Editor", it is a word processing program.

"Simple Text Editors" are exactly that, they let you simply edit text.

---

### Post by kaligus on 2010-03-08
> **Kaligo said:**
> Abiword is supposed to be a simple, lightweight alternative to OO Writer.  Haven't used it in years though, so can't speak of it's current state.

no syntax highlighting :( otherwise I think I would suggest it, loads quick, spell as you go, simple suggestions for spelling.

---

### Post by kaligus on 2010-03-08
> **dcstar said:**
> Something that does spell checking is not a "Simple Text Editor", it is a word processing program.

"Simple Text Editors" are exactly that, they let you simply edit text.

There is a great deal of real-estate between your definition and say OpenOffice.  On one end of that line is "dirt simple, featureless" on the other end is "way too much going on for the need"

Err on the side of simple and let's not start a religious or politics argument yes?

---

### Post by dcstar on 2010-03-08
> **kaligus said:**
> There is a great deal of real-estate between your definition and say OpenOffice.  On one end of that line is "dirt simple, featureless" on the other end is "way too much going on for the need"

Err on the side of simple and let's not start a religious or politics argument yes?

It's not "religion" or "politics", it's having an accurate description in the thread title so people can clearly communicate a problem.

There may well be someone who looks at the forums who knows of a simple word processor that may do the job, but doesn't even bother to read this thread because they know what a "SIMPLE small text editor" is.

A lot of people just don't have the time to read the contents of every thread, as those time-wasters who post "I have a problem" find out when their thread has no responses after many days.

---

### Post by mdebusk on 2010-03-08
> **kaligus said:**
> I am looking for an editor to fill a specific request for a mostly non-computer person.  He uses a computer to write manuals and other books for classes he teaches.  He has come to ubuntu so he can more easily access updates, gimp, etc. than he felt he could in Windows.

Well, *my* curiosity is piqued: what was he using *before*?

I'm inclined to agree with the rest here in that it's a word processor, probably AbiWord, that he needs. Any word processor will *appear to* load quickly, though, if he leaves it open and minimized. This solves the first two.

Regarding the "syntax highlighting": for what purpose? Syntax highlighting in a programmer's editor is for catching syntax errors before the debugger is brought into play; is it absolutely required that he have this feature "inline," or could some sort of post-processing macro in the word processor do the job?

FWIW, if he spends a lot of time writing, or if his work depends on what he writes, he should invest the time and effort required to master either a good word processor or LaTeX.

---

### Post by mdebusk on 2010-03-08
Delete this, please...

---

### Post by kaligus on 2010-03-08
> **dcstar said:**
> It's not "religion" or "politics", it's having an accurate description in the thread title so people can clearly communicate a problem.

There may well be someone who looks at the forums who knows of a simple word processor that may do the job, but doesn't even bother to read this thread because they know what a "SIMPLE small text editor" is.

A lot of people just don't have the time to read the contents of every thread, as those time-wasters who post "I have a problem" find out when their thread has no responses after many days.

Then possibly some extra information for us dummies instead of what looks and smells like nit-picking over where the line is drawn would help avoid misunderstandings?

I thought simple was 3 features not thousands and nobody ever told me that there was a requirement that once you add feature-x you had to change the question.

The definition of a word processor in my dictionary versus a text editor tells me what we are looking for is a text editor far from a word processor.

---

### Post by mdebusk on 2010-03-08
> **kaligus said:**
> The definition of a word processor in my dictionary versus a text editor tells me what we are looking for is a text editor far from a word processor.

It isn't *your* "dictionary" you should use in this instance, though, but that of your *friend*. And since he's writing books and papers, he needs a word processor... not a text editor. The need for inline spell-checking only reinforces that.

The monkeywrench is what you describe as "syntax highlighting." If we knew what that would do for your friend -- what specific problem it would solve -- it might be easier.

---

### Post by kaligus on 2010-03-08
> **mdebusk said:**
> Well, *my* curiosity is piqued: what was he using *before*?

I'm inclined to agree with the rest here in that it's a word processor, probably AbiWord, that he needs. Any word processor will *appear to* load quickly, though, if he leaves it open and minimized. This solves the first two.

Regarding the "syntax highlighting": for what purpose? Syntax highlighting in a programmer's editor is for catching syntax errors before the debugger is brought into play; is it absolutely required that he have this feature "inline," or could some sort of post-processing macro in the word processor do the job?

FWIW, if he spends a lot of time writing, or if his work depends on what he writes, he should invest the time and effort required to master either a good word processor or LaTeX.

He was using crimson editor + lexispell + a little thing that loads crimson and gives you a hot key to focus it on top of your desktop. (lexispell which I hope I have spelled correctly is a spell checker that checks any Windows text box in any program that uses the MS API calls and controlls).

The problem is that for 99% of what he writes a full blown word processor has too much going on, can not be accessed at a moments notice (without taking up lots of memory), and requires thought when saving the file to make sure it gets saved as "text" not "ods" or "doc" or whatever.

These documents he writes quite a few of per day projects for engineers of one kind or another at the company he works for.  These manuals change per project and this can happen several times a day to once a week.  He will teach the class for the project, sit down and write the next set (same keywords 99% of the time), rinse and repeat.  It may be for as few as 5 people and as many as 20 at a time.

The keywords he has set up his previous editor to highlight for him are a convenience thing that he has gotten so used to he has decided he can't live without.  You look at a line and see the right number of colors, in the correct order and you move to the next line.  Errors are reduced (but not eliminated).

---

### Post by lemuriaX on 2010-03-08
It seems like if you customized gedit (I know it's on your list of already rejected) it could maybe do what you need.

Poking around a bit, it looks like you can create custom syntax hightlighting:

[http://live.gnome.org/Gedit/NewLanguage](http://live.gnome.org/Gedit/NewLanguage)

Spell check as you type is a built in option. Anyways, just an idea if you haven't explored this yet.

---

### Post by mdebusk on 2010-03-08
> **kaligus said:**
> The problem is that for 99% of what he writes a full blown word processor has too much going on, can not be accessed at a moments notice (without taking up lots of memory), and requires thought when saving the file to make sure it gets saved as "text" not "ods" or "doc" or whatever.

For the applications you've described -- he's not actually writing for publication, which I took him to be doing -- a text editor would work if you can find one he likes that does inline spell-check. I know gedit does, with the proper plug-in, and one can create specialized syntax highlighting; why has he rejected it?

You might also refer him to [bluefish]("http://bluefish.openoffice.nl/"). It recently hit version 2.0.

---

### Post by kaligus on 2010-03-08
> **mdebusk said:**
> For the applications you've described -- he's not actually writing for publication, which I took him to be doing -- a text editor would work if you can find one he likes that does inline spell-check. I know gedit does, with the proper plug-in, and one can create specialized syntax highlighting; why has he rejected it?

You might also refer him to [bluefish]("http://bluefish.openoffice.nl/"). It recently hit version 2.0.

He rejected gedit because the auto-spell-check is not sticky but I started looking at that bit as well as finding a way he doesnt need to be root to edit his "language" files.

I am not getting on well with the git pull I just did but will give the tarball a go when I am back on the other side of the clock :)

---

### Post by kaligus on 2010-03-09
Thank you all for the help (and the extra information along the way).

I am going to work on getting gedit to compile so that the auto-spell-check can be made to default "on"

My friend is a little unsure that he wants to mess with XML files but it looks simple enough to him so for now he is using gedit with a sticky to remind himself to tick the auto-check box.

---

