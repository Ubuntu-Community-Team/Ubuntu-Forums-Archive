---
title: "enabling indentation in VIM when using python"
date: 2011-02-09
forum: General Help
---

### Post by genjix on 2011-02-09
Recent reinstall of latest Ubuntu.

I installed vim-nox which apparently installs vim-python

/usr/share/vim/plugins doesn't exist

Python doesn't indent properly eventhough I'm using the same vimrc from the previous Ubuntu version.

Any ideas?

Thanks

---

### Post by genjix on 2011-02-10
bump

---

### Post by gmargo on 2011-02-10
The default plugins are in /usr/share/vim/vim72/plugin/

---

### Post by genjix on 2011-02-10
Thanks. That's so confusing.
> genjix@l:~$ ls /usr/share/vim/vim72/plugin/
getscriptPlugin.vim  matchparen.vim   README.txt    spellfile.vim  tohtml.vim         zipPlugin.vim
gzip.vim             netrwPlugin.vim  rrhelper.vim  tarPlugin.vim  vimballPlugin.vim


It doesn't seem to exist! vim-python is marked as virtual and says I need to install vim-nox, vim-gnome or vim-gtk... I have installed vim-nox.

When running sudo aptitude install vim-python nothing happens.

---

### Post by gmargo on 2011-02-10
> **genjix said:**
> That's so confusing. It doesn't seem to exist! 

What doesn't exist?  There is no "vim-python" command to find.

---

### Post by genjix on 2011-02-12
I mean the vim-python package...

Is this a bug? Any ideas what to do?

thanks

---

### Post by gmargo on 2011-02-12
By installing the **vim-nox** package, you already have python support.  **vim-nox** provides the virtual package called **vim-python**.  

I think you're confused about the "python" part.  In the vim case, "vim-python" means that this particular **vim** binary has support for a **python** API - meaning that **vim** scripts can run **python** code.  This is completely separate from **vim**'s ability to do syntax highlighting and automatic code indentation.

The bottom line is that you have all you need installed already.  I think the original subject was that indentation of python code was not working properly using your old .vimrc file.  Perhaps it is some setting in that file?  Or no indentation options are enabled?

---

### Post by genjix on 2011-02-13
The point is that I never needed those options before. It's the exact same .vimrc I had before I reinstalled.

If I enable autoindent then it's a semi-working substitute... lines don't indent after : and do indent after break/return ... in my old install vim did not do this and didn't need autoindent enabled.

---

### Post by genjix on 2011-02-13
ok so I installed vim-scripts and saw a new plugin in indent/python.vim
:source /usr/share/vim-scripts/indent/python.vim
and had correct indentation.

Then I add to .vimrc
" load indenting
autocmd BufRead *.py source /usr/share/vim-scripts/indent/python.vim

---

### Post by gmargo on 2011-02-14
There are many indentation options.  The simplest method of enabling automatic indentation with filetype recognition is to run the command ":filetype indent on" (or put in .vimrc).

Perhaps all you need is the 'smartindent' or 'cindent' option.

See the vim :help for much more information.  In particular:

```

:help 30.2                         " Indenting C style text
:help 30.3                         " Automatic indenting
:help indent.txt                   " lots more indenting info

```

---

### Post by genjix on 2011-03-02
> **gmargo said:**
> There are many indentation options.  The simplest method of enabling automatic indentation with filetype recognition is to run the command ":filetype indent on" (or put in .vimrc).

Perhaps all you need is the 'smartindent' or 'cindent' option.

See the vim :help for much more information.  In particular:

```

:help 30.2                         " Indenting C style text
:help 30.3                         " Automatic indenting
:help indent.txt                   " lots more indenting info

```

Thanks, but this is not proper Python indenting. The fix was as I detailed above. You have to load the Python indenting script manually (must have been disabled since last release):

:source /usr/share/vim-scripts/indent/python.vim

---

### Post by genjix on 2011-03-05
OK, I have a new Ubuntu install.

Installing vim-gtk vim-scripts and doing set smartindent makes it work. (you still get terminal vim with vim-gtk).

So I recommend to install vim-gtk instead of vim-nox for others.

---

### Post by genjix on 2011-03-31
OK, so I've been using that for a while and only just found the proper fix this morning:

filetype indent on

You don't need smartindent or anything.

---

### Post by I3igfoot on 2011-05-24
Yay! Adding **filetype indent on** to **~/.vimrc** totally enabled the indentation! (I already had **vim-scripts** installed; I also installed **vim-addon-manager** and ran **vim-addons install python-indent** but this didn't help.)

---

