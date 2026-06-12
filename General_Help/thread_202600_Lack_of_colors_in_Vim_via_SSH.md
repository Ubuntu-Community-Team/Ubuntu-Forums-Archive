---
title: "Lack of colors in Vim via SSH"
date: 2006-06-23
forum: General Help
---

### Post by treesize on 2006-06-23
I'm using PuTTY to log in to my Ubuntu 6.06 install from Windows. Once there I want to use Vim to edit config files and such.

The default color scheme was pretty horrible, so I went to this site:
[http://www.cs.cmu.edu/~maverick/VimColorSchemeTest/index-html.html](http://www.cs.cmu.edu/~maverick/VimColorSchemeTest/index-html.html)

My problem is that I can't get the colors to look like the previews on the site.

Google tells me that I need to change the terminal type somehow, but doing an 'export TERM=xterm-color' doesn't really help. How do I make Vim (and PuTTY, I guess) show me the proper colors?

---

### Post by scxtt on 2006-06-23
create a file in your ~ directory called .vimrc, paste the following in:
[indent]syntax on[/indent]of course this assumes you're getting any color @ all ...

btw, i'm using putty right now from a windows box to dapper ...

---

### Post by treesize on 2006-06-23
Sorry about not being clear enough; I *am* getting colors. Just not the right ones.

Have you tried using a custom colorscheme in Vim? Can you get, say, the Desert256 scheme to look similar to the example on the site I linked to above?

---

### Post by treesize on 2006-06-24
This has to be solvable, right? I can't be the only one who wants nice Vim colors.

---

### Post by nuzzy on 2006-06-24
Dunno if this helps, but I read thru the vim manpage and set my terminal to green on black (to test the dark *advantage.vim* I picked from the page you linked).  I then typed:

"**vim -S advantage.vim*** **filename***"

and it looks like it worked.  I'm sure there's an easier way or even a way to alias/add it to .vimrc but I haven't explored it yet.

edit: for your desert256 scheme look here:

[http://www.vim.org/scripts/script.php?script_id=1243](http://www.vim.org/scripts/script.php?script_id=1243)

You'll need to follow on how to make the background the way it's supposed to be, then add

:colorscheme desert256

to your .vimrc file *or* while in vim type **:colorscheme desert256** to get your colorscheme

---

### Post by treesize on 2006-06-24
I have tried that, but I'm still not satisfied with the colors. They don't look anything like  the colors on the site do.

I guess my main question is whether or not it's possible to squeeze more than 256 colors out of the console. I'd hoped just to give it a bunch of RGB values and that would be that, but it doesn't look like that's possible.

---

### Post by elamericano on 2006-07-27
It appears that people did not understand. The color schemes show up correctly in gvim, but in gnome-terminal (xterm) the colors are changed. It seems gnome-terminal is in 16-color mode.

Is there a way to change to 256-color mode, and hopefully have the color schemes show correctly?

---

### Post by elamericano on 2006-07-27
I tried xterm, which displays all 256 colors using this colortest:

[http://www.vim.org/scripts/script.php?script_id=1349](http://www.vim.org/scripts/script.php?script_id=1349)

but vim still doesn't display the colors right. I used a 256-color theme. I still don't have the color depth of gvim, so I'm not expecting them to look the same, but it's clearly stuck in 16 color mode. That awful pink and teal combo is immediately visible. I read where I have to set TERM=xterm-256color, but that was not recognized by vim.

So now the question is the original question. How do we get 256-color support in vim?

(I'll pursue gnome-terminal being only 16 colors in a different thread.)

---

### Post by elamericano on 2006-07-29
Finally! In order to get 256 colors in vim in a terminal you can do:

xterm (switch to the xterm window when it comes up.)
vi <filename>
:syntax enable
:set t_Co=256
:colors desert256 (or your own 256 color theme)

Most themes won't work in 256 colors correctly. There are some 256-color schemes and a converter for gvim schemes at the previously mentioned site: [http://frexx.de/xterm-256-notes/](http://frexx.de/xterm-256-notes/)

Great. Now to find out how hard it is to make gnome-terminal 256 colors. I hope we get easy access to this feature in edgy.

My vim screen is attached:

---

### Post by treesize on 2006-07-30
Thanks mate, I'll give that a try.

---

### Post by elamericano on 2006-07-31
I have it working in gnome-terminal too. I had to compile vte-0.13.4 and gnome-terminal 2.15.1. I'll put together a HowTo, and add a link here when I'm done.

I'm also working on a better converter. The one on the site only translates one color. My perl script will convert an entire colorscheme file.

---

### Post by Micah Elliott on 2007-08-29
> **elamericano said:**
> Finally! In order to get 256 colors in vim in a terminal you can do:

xterm (switch to the xterm window when it comes up.)
vi <filename>
:syntax enable
:set t_Co=256
:colors desert256 (or your own 256 color theme)


My problem was that I had "TERM=xterm-256color".  Vim seems very unhappy no matter what I do from there.  However, setting "TERM=xterm" and then adding "set t_Co=256" in my .vimrc made vim happily using 256 colors!!

:hi

The lesson I've learned is that various tools get upset if TERM is set to xterm-256color (mutt, less, vim, what others??).  But some tools do great, like elinks.  So I will just maintain aliases for those tools that accept the 256 in TERM, e.g., "alias elinks='TERM=xterm-256color elinks'".

Now maybe I can make my gvim-specific adobe vim theme xterm-friendly!

> **elamericano said:**
> My vim screen is attached:

Great screen!  What did you do to turn on that leftnav file browser?

---

