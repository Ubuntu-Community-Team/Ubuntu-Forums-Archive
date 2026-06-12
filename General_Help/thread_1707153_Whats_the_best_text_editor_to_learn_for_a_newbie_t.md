---
title: "Whats the best text editor to learn for a newbie that will be working in programming?"
date: 2011-03-14
forum: General Help
---

### Post by btf18 on 2011-03-14
Hey,

I'm just learning scripting and have gone through the whole tutorial for the text editor vim, and written my first script in it. However its harrrrd to get the hang of. My scripting tutorial page says vim is notorious for being unintuitive, so is hard to learn. Is vim really the best, and is there a more intuitive text editor that is more widely used and better? 

The tutorial mentioned emacs, saying its the giant of the text editor world, is it any easier to learn? Should i just start with a smaller easier text editor that is very basic? If so, i would still like to know what text editor skills is the programming industry demanding of its programmers, as in what text editor do they want you to use? 

Thanks

---

### Post by WlaadDyaab on 2011-03-14
Text editor for programming languages as in: something like Note pad?

If you mean a "Compiler", I heard that Code Blocks IDE (I think only for C and C++ (programming language)) is good

---

### Post by btf18 on 2011-03-14
I mean like vim and emacs, if the ones you suggested are the same type of program, they will definitely be worth checking out, thanks. Sorry im new to programming so dont know what im talking about, but basically i was under the impression the language was just called command line maybe. The text editor takes over the terminal and looks similar to the terminal. Its just shell scripting. writing shell scripts. It might not be used in the industry, just personal use, not sure, but someone was telling me they use vim in the industry. My course has just started and its postponed due to an earthquake and idk when it starts so im leaping ahead..

---

### Post by WlaadDyaab on 2011-03-14
> **btf18 said:**
> I mean like vim and emacs, if the ones you suggested are the same type of program, they will definitely be worth checking out, thanks. Sorry im new to programming so dont know what im talking about, but basically i was under the impression the language was just called command line maybe. The text editor takes over the terminal and looks similar to the terminal. Its just shell scripting. writing shell scripts. It might not be used in the industry, just personal use, not sure, but someone was telling me they use vim in the industry. My course has just started and its postponed due to an earthquake and idk when it starts so im leaping ahead..

Oh nooo don't worry, I'm also new but only that I've been using Linux for around 1 year, so I know only a little bit and VERY happy to help you understand your way around :)

"Command line" as I understand it is "the background of the operating system". And that you're not inventing anything new unless you open a program from the command line and do the editing (what I would call; for the time being "inventing")

Command lines are technical and ugly (for beginner phrases)

On Microsoft Windows they have their own command line called "MS DOS"

On Linux it's called "Terminal" (and never mind other phrases/nicknames for the time being)

But when I said earlier "compiler". Now that's another thing:

Command line is the program that's inside a big program called "operating system" (i.e. Microsoft Windows XP, Microsoft Windows Vista, Microsoft Windows 7, Mac OS X ("X" means "10" in Greek), Unix, Linux, Solaris...etc)

"Compiler" is the program that lets us create any program, even the big program known as "operating system"

Compilers are "inventors"

Comand lines are "programs that let see the background (the real form) of the operating system"

Is that OK up to now?

So when I said "Code Blocks IDE". That's only one type of a compiler

---

### Post by wojox on 2011-03-14
Terminally  Vim

Graphically  gVim

---

### Post by WlaadDyaab on 2011-03-14
> **wojox said:**
> Terminally  Vim

Graphically  gVim

wojox do you mean that Terminal is User interface? I don't understand what's "Vim" and "gVim"

---

### Post by ScottishGirl on 2011-03-15
I use Nano for bash scripts and general work.   Jedit is a good editor for programing.

---

### Post by btf18 on 2011-03-15
Thanks. Im not that new. Im new to scripting. text editor is the common term for what i am looking for. It creates scripts that give the shell complex and powerful commands. Youre probably thinking of something else. cheers

---

### Post by WlaadDyaab on 2011-03-15
> **btf18 said:**
> Thanks. Im not that new. Im new to scripting. text editor is the common term for what i am looking for. It creates scripts that give the shell complex and powerful commands. Youre probably thinking of something else. cheers

I bought the previous edition (2010) to this book:

[http://www.bookbutler.com/search.html?searchFor=0672333449&searchBy=isbn&searchIn=uk&sortBy=salesrank&amountIn=gbp&shipTo=gb&zip=&showMore=true&pageNr=1](http://www.bookbutler.com/search.html?searchFor=0672333449&searchBy=isbn&searchIn=uk&sortBy=salesrank&amountIn=gbp&shipTo=gb&zip=&showMore=true&pageNr=1)

That's how I even got to know that there's a Forum for Ubuntu (ubuntuforums.org) :)

---

### Post by btf18 on 2011-03-15
Cheers all. Thinking about starting on nano and then learning vim when i'm more competent. Any explanation as to why vim is better than emacs? Personal preference kinda thing?

---

### Post by wojox on 2011-03-15
> **WlaadDyaab said:**
> wojox do you mean that Terminal is User interface? I don't understand what's "Vim" and "gVim"

Vim you just open gnome-terminal or any terminal:

Inside /home directory

```
vim myScript
```

Outside /home directory

```
sudo vim /etc/X11/xorg.conf
```

gVim is the same way, except it's graphical. Like Gedit.

To edit inside your home directory just open the editor from the menu.

For outside your /home directory

```
gksudo gvim /etc/X11/xorg.conf
```

---

### Post by wojox on 2011-03-15
> **btf18 said:**
> Cheers all. Thinking about starting on nano and then learning vim when i'm more competent. Any explanation as to why vim is better than emacs? Personal preference kinda thing?

Because no matter where you go Unix/Linux vi is always the default and installed.

---

### Post by WlaadDyaab on 2011-03-15
> **wojox said:**
> Vim you just open gnome-terminal or any terminal:

Inside /home directory

```
vim myScript
```

Outside /home directory

```
sudo vim /etc/X11/xorg.conf
```

gVim is the same way, except it's graphical. Like Gedit.

To edit inside your home directory just open the editor from the menu.

For outside your /home directory

```
gksudo gvim /etc/X11/xorg.conf
```

Oh thanks now I get it :)

Sorry for my big mouth Lol, I just have one other question:

You know when everyone here on the forum posts something similar to what you mentioned in this post: "Inside /home directory"

Do they/you mean that there has to be a command like "sudo" before "/home directory"?

Sorry, I just didn't understand that and thought maybe this is the right moment to ask

---

### Post by jerome1232 on 2011-03-15
Vim vs Emacs is a on going holy war. It seems the majority of users on this forum prefer vim.

Vim is confusing at first but after you go through vim tutor, get it setup a bit and try using it's features to your advantage, it becomes second nature rather fast.

---

### Post by wojox on 2011-03-15
> **WlaadDyaab said:**
> Oh thanks now I get it :)

Sorry for my big mouth Lol, I just have one other question:

You know when everyone here on the forum posts something similar to what you mentioned in this post: "Inside /home directory"

Do they/you mean that there has to be a command like "sudo" before "/home directory"?

Sorry, I just didn't understand that and thought maybe this is the right moment to ask

My home is /home/wojox/, it sits off of root. Anything I wish to edit inside MY directory and can without sudo permissions. 

It's only when I need to edit a file outside of my home. Like /etc/X11/.xorg.conf or /etc/default/grub that I need sudo permissions. Have a look at this [RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by Old *ix Geek on 2011-03-15
Use whatever you're comfortable with. Personally, I've been at this for so long...back when I started, vi involved chisels and stone tablets. :eek: :lolflag:  Anyway, I always fall back to using vi (and I call it that, too, I don't care if it's now vim), because it's so ingrained in me I can operate it in my sleep.

But that doesn't stop me from also using some nice graphical editors, especially when I'm coding web pages and want to have nifty features like syntax highlighting, automatic brackets, and so on. I like, and normally use, KWrite for that.

There's nothing magical about code. As long as the editor you use works well FOR YOU, that's all you need.

---

### Post by btf18 on 2011-03-15
Thanks all. Everyone seems to pick up a few text editors. Once you have learnt vim, is it the same level of difficulty to learn another text editor? As in, are they completely different in the commands you give the editor (:w FILENAME to save etc for vim, usually always different command to save etc for all the others?)

---

### Post by wojox on 2011-03-15
> **btf18 said:**
> Thanks all. Everyone seems to pick up a few text editors. Once you have learnt vim, is it the same level of difficulty to learn another text editor? As in, are they completely different in the commands you give the editor (:w FILENAME to save etc for vim, usually always different command to save etc for all the others?)

Yes there pretty much diffrent.

To close and save vi I use Esc :wq!

In nano it's Ctrl+O, Ctrl+X

---

### Post by btf18 on 2011-03-15
Seems best to just learn the one you can do the most on, and spend your other time coding rather than learning another editor xP But i understand about trying out different ones to see what you like. Thanks all. Vim seems a good option as its fairly universal, popular and comprehensive. Cheers

---

### Post by 5149.5 on 2011-03-15
I cast another vote for vi/vim/gvim. When writing scripts, you can save your work and exit to the shell with 5 keystrokes. Then you can immediately type in the script name and execute it. No need to reach for the darn mouse. It only takes a couple hours of script writing and you will have the keystrokes for vi down pat. Until then put a little cheat sheet on the side of your terminal.

---

### Post by btf18 on 2011-03-15
Thanks Dan! Im excited about Vim!

---

### Post by aero13972486 on 2011-03-23
Vim is nice to work with in the terminal. Easy on the eyes. EMacs looks horrible.

But when it comes to copying and pasting text between multiple documents, I really miss my cracked version of UltraEdit when I had windows :(
Mouse and keyboard working together was really productive. Intuitive switching between document tabs, and you didn't have to remember whole bunch of key combinations. Who has time for this? Its kinda like Chrome vs Firefox. Chrome is so much neater and more space for the page, but sometimes you just feel out at sea with everything so skeletal. Know what I mean?

GVim beats UltraEdit with programmatic power, but as far as the UI goes, they've got some thinking to do. For a Windows user I still open documents in GEdit.
Ya

---

### Post by btf18 on 2011-03-26
Thanks. Im now doing some windows programming as i'm just going through a book. Havent started yet but it sounds like it's an easy language, BASIC, and will get me into it quicker

---

### Post by dandnsmith on 2011-03-26
Not wishing to decry it, but BASIC isn't like any other programming language, and has lots of limitations.

My favourite editor for linux is vi(m) - I found I couldn't keep all the rather abstruse commands for emacs in my head, but could retain enough of the vi/sed repertoire to do things (even if not optimally). sed is the command line editor which can be invoked from vi to get complicated things done.

The choice of language for programming, and editor, has to depend on where you see yourself going with your attempt - any formal course will have its own route.

---

