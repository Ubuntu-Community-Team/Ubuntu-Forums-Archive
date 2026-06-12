---
title: "4nt-like command line completion?"
date: 2011-03-21
forum: General Help
---

### Post by Rebelli0us on 2011-03-21
Is it possible to have command line completion similar to 4nt?  

In Terminal you have to type most of the name before it will complete for you, otherwise it just displays a list of names. Are you supposed to read from there and copy filenames? And the upper/lower case stuff is really ugly. Is there a smart command line utility that can build the entire path for you, **and** recall history based on a partial string?

---

### Post by oldos2er on 2011-03-21
I don't know what 4nt is, but bash Tab completion is configurable. 

[http://joggie.nl/2010/08/18/ubuntu-bash-completion/](http://joggie.nl/2010/08/18/ubuntu-bash-completion/)

[http://embraceubuntu.com/2006/01/28/turn-on-bash-smart-completion/](http://embraceubuntu.com/2006/01/28/turn-on-bash-smart-completion/)

[http://www.debian-administration.org/articles/316](http://www.debian-administration.org/articles/316)

Ctrl-r allows you to search history, [http://www.catonmat.net/blog/the-definitive-guide-to-bash-command-line-history](http://www.catonmat.net/blog/the-definitive-guide-to-bash-command-line-history)

---

### Post by Rebelli0us on 2012-12-26
Here’s a little Christmas gift for the thousands (or millions) of 4NT users.

For 4NT  and “Take Command” users, the bash command line is user-hostile, unless you can memorize a lot of trivia. To emulate the basic functionality of the 4NT command line, create a file named “.inputrc” in your home directory with the following content.

Some things still don’t work (as per my comments), so feel free to help. For example, TAB cycles through filenames but  will not reverse with Shift+Tab.


```
# ~/.inputrc -- Emulate the basic functionality of JP Software’s 4NT command line.

ESCAPE: kill-whole-line			# Escape twice clears line -- How does single Esc work??

# Delete from cursor to beginning/end of line
##"\e[1;5H": backward-kill-line	# Ctrl+Home -- Doesn't work
##"\e[1;5F": kill-line			# Ctrl+End  -- Doesn't work

"\e[1;6D": backward-kill-line	# Ctrl+Shift+Left
"\e[1;6C": kill-line			# Ctrl+Shift+Right

"\e[1;2D": backward-kill-word	# Shift+Left
"\e[1;2C": kill-word			# Shift+Right

##"\e[1;3D": backward-delete-char	# Alt+Left
##"\e[1;3C": delete-char			# Alt+Right


##### Filename Completion #####
set completion-ignore-case on	# ignore case on completion. -- Doesn't work
set mark-directories on			# append slash to dirs.      -- Doesn't work
set visible-stats on			# ls -F completion
##"\C-i": menu-complete			# Tab cycles through filenames instead of listing. -- Reverse with Shift+Tab??
TAB: menu-complete
set show-all-if-ambiguous on	# list possible completions instead of ringing bell
set show-all-if-unmodified on
set mark-symlinked-directories on
set match-hidden-files off		# same as typing * before Tab
set bell-style none				# no bell on tab-completion
set skip-completed-text on


##### Command History Recall #####
# Up/Down recalls previous/next command or the most recent command that matches a partial command line.
"\e[A": history-search-backward
"\e[B": history-search-forward
set revert-all-at-newline on	# Disallow modifying history
set history-preserve-point on
set history-size 10000
# Page Up/Down = beginning/end of history -- Doesn't work
"\e[5~": history-search-backward	# beginning-of-history
"\e[6~": history-search-forward		# end-of-history

# Insert/Delete keys don't work without this. -- Why?
"\e[2~": overwrite-mode			# How to change cursor shape to indicate overwrite mode???
"\e[3~": delete-char

# Ctrl+Left/Right doesn't work without this. -- Why? 
"\e[1;5D": backward-word
"\e[1;5C": forward-word



# Home/End
#"\e[1~": beginning-of-line
#"\e[4~": end-of-line
#"\e[H": beginning-of-line
#"\e[F": end-of-line


```

---

### Post by overdrank on 2012-12-26
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

