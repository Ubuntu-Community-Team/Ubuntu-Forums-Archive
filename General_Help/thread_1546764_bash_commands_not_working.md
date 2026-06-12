---
title: "bash commands not working"
date: 2010-08-05
forum: General Help
---

### Post by Folk Theory on 2010-08-05
when I type CTRL A in bash, instead of being taken to the first character in the line, the characters "^A" appear. the same happens with ^E, ^F , ^B and ^L. 

However, ^H works fine.

Is there some way to fix this?

---

### Post by chopinhauer on 2010-08-06
What terminal are you using? Is your TERM variable set correctly?

---

### Post by Folk Theory on 2010-08-06
my terminal is ubuntu's default: gnome-terminal, using bash. However using 
echo $TERM returns xterm. Is this the root of the problem? what should I do?

---

### Post by chopinhauer on 2010-08-06
> **Folk Theory said:**
> 
my terminal is ubuntu's default: gnome-terminal, using bash. However using 
echo $TERM returns xterm. Is this the root of the problem? what should I do?


'xterm' is the correct value for the terminal type of **gnome-terminal**. The next step would be to check **readline** key bindings, you can check it with:
```
bind -p
```
and look if '\C-a' is bound to something.

---

### Post by Folk Theory on 2010-08-06
it's huge, here it goes:

# abort (not bound)
"\C-j": accept-line
"\C-m": accept-line
# alias-expand-line (not bound)
# arrow-key-prefix (not bound)
# backward-byte (not bound)
"\eOD": backward-char
"\e[D": backward-char
"\C-h": backward-delete-char
"\C-?": backward-delete-char
# backward-kill-line (not bound)
# backward-kill-word (not bound)
# backward-word (not bound)
# beginning-of-history (not bound)
"\eOH": beginning-of-line
"\e[H": beginning-of-line
# call-last-kbd-macro (not bound)
# capitalize-word (not bound)
# character-search (not bound)
# character-search-backward (not bound)
# clear-screen (not bound)
"\C-i": complete
# complete-command (not bound)
# complete-filename (not bound)
# complete-hostname (not bound)
# complete-into-braces (not bound)
# complete-username (not bound)
# complete-variable (not bound)
# copy-backward-word (not bound)
# copy-forward-word (not bound)
# copy-region-as-kill (not bound)
# dabbrev-expand (not bound)
"\e[3~": delete-char
# delete-char-or-list (not bound)
# delete-horizontal-space (not bound)
# digit-argument (not bound)
# display-shell-version (not bound)
# do-lowercase-version (not bound)
# downcase-word (not bound)
# dump-functions (not bound)
# dump-macros (not bound)
# dump-variables (not bound)
# dynamic-complete-history (not bound)
# edit-and-execute-command (not bound)
# emacs-editing-mode (not bound)
# end-kbd-macro (not bound)
# end-of-history (not bound)
"\eOF": end-of-line
"\e[F": end-of-line
# exchange-point-and-mark (not bound)
# forward-backward-delete-char (not bound)
# forward-byte (not bound)
"\eOC": forward-char
"\e[C": forward-char
"\C-s": forward-search-history
# forward-word (not bound)
# glob-complete-word (not bound)
# glob-expand-word (not bound)
# glob-list-expansions (not bound)
# history-and-alias-expand-line (not bound)
# history-expand-line (not bound)
# history-search-backward (not bound)
# history-search-forward (not bound)
# insert-comment (not bound)
# insert-completions (not bound)
# insert-last-argument (not bound)
# kill-line (not bound)
# kill-region (not bound)
# kill-whole-line (not bound)
# kill-word (not bound)
# magic-space (not bound)
"\C-n": menu-complete
"\C-p": menu-complete-backward
"\eOB": next-history
"\e[B": next-history
# non-incremental-forward-search-history (not bound)
# non-incremental-forward-search-history-again (not bound)
# non-incremental-reverse-search-history (not bound)
# non-incremental-reverse-search-history-again (not bound)
# old-menu-complete (not bound)
# operate-and-get-next (not bound)
# overwrite-mode (not bound)
# possible-command-completions (not bound)
# possible-completions (not bound)
# possible-filename-completions (not bound)
# possible-hostname-completions (not bound)
# possible-username-completions (not bound)
# possible-variable-completions (not bound)
"\eOA": previous-history
"\e[A": previous-history
"\C-v": quoted-insert
# redraw-current-line (not bound)
# re-read-init-file (not bound)
"\C-r": reverse-search-history
# revert-line (not bound)
"\C-a": self-insert
"\C-b": self-insert
"\C-c": self-insert
"\C-e": self-insert
"\C-f": self-insert
"\C-g": self-insert
"\C-k": self-insert
"\C-l": self-insert
"\C-o": self-insert
"\C-q": self-insert
"\C-x": self-insert
"\C-z": self-insert
"\C-\\": self-insert
"\C-]": self-insert
"\C-^": self-insert
" ": self-insert
"!": self-insert
"\"": self-insert
"#": self-insert
"$": self-insert
"%": self-insert
"&": self-insert
"'": self-insert
"(": self-insert
")": self-insert
"*": self-insert
"+": self-insert
",": self-insert
"-": self-insert
".": self-insert
"/": self-insert
"0": self-insert
"1": self-insert
"2": self-insert
"3": self-insert
"4": self-insert
"5": self-insert
"6": self-insert
"7": self-insert
"8": self-insert
"9": self-insert
":": self-insert
";": self-insert
"<": self-insert
"=": self-insert
">": self-insert
"?": self-insert
"@": self-insert
"A": self-insert
"B": self-insert
"C": self-insert
"D": self-insert
"E": self-insert
"F": self-insert
"G": self-insert
"H": self-insert
"I": self-insert
"J": self-insert
"K": self-insert
"L": self-insert
"M": self-insert
"N": self-insert
"O": self-insert
"P": self-insert
"Q": self-insert
"R": self-insert
"S": self-insert
"T": self-insert
"U": self-insert
"V": self-insert
"W": self-insert
"X": self-insert
"Y": self-insert
"Z": self-insert
"[": self-insert
"\\": self-insert
"]": self-insert
"^": self-insert
"_": self-insert
"`": self-insert
"a": self-insert
"b": self-insert
"c": self-insert
"d": self-insert
"e": self-insert
"f": self-insert
"g": self-insert
"h": self-insert
"i": self-insert
"j": self-insert
"k": self-insert
"l": self-insert
"m": self-insert
"n": self-insert
"o": self-insert
"p": self-insert
"q": self-insert
"r": self-insert
"s": self-insert
"t": self-insert
"u": self-insert
"v": self-insert
"w": self-insert
"x": self-insert
"y": self-insert
"z": self-insert
"{": self-insert
"|": self-insert
"}": self-insert
"~": self-insert
"\200": self-insert
"\201": self-insert
"\202": self-insert
"\203": self-insert
"\204": self-insert
"\205": self-insert
"\206": self-insert
"\207": self-insert
"\210": self-insert
"\211": self-insert
"\212": self-insert
"\213": self-insert
"\214": self-insert
"\215": self-insert
"\216": self-insert
"\217": self-insert
"\220": self-insert
"\221": self-insert
"\222": self-insert
"\223": self-insert
"\224": self-insert
"\225": self-insert
"\226": self-insert
"\227": self-insert
"\230": self-insert
"\231": self-insert
"\232": self-insert
"\233": self-insert
"\234": self-insert
"\235": self-insert
"\236": self-insert
"\237": self-insert
"&#65533;": self-insert
"&#65533;": self-insert
"&#65533;": self-insert
"&#65533;": self-insert
"&#65533;": self-insert
"&#65533;": self-insert
"&#65533;": self-insert
"&#65533;": self-insert
"&#65533;": self-insert
"&#65533;": self-insert
"&#65533;": self-insert
"&#65533;": self-insert
"&#65533;": self-insert
"&#65533;": self-insert
"&#65533;": self-insert
"&#65533;": self-insert
"&#65533;": self-insert
"&#65533;": self-insert
"&#65533;": self-insert
"&#65533;": self-insert
"&#65533;": self-insert
"&#65533;": self-insert
"&#65533;": self-insert
"&#65533;": self-insert
"&#65533;": self-insert
"&#65533;": self-insert
"&#65533;": self-insert
"&#65533;": self-insert
"&#65533;": self-insert
"&#65533;": self-insert
"&#65533;": self-insert
"&#65533;": self-insert
"&#65533;": self-insert
"&#65533;": self-insert
"&#65533;": self-insert
"&#65533;": self-insert
"&#65533;": self-insert
"&#65533;": self-insert
"&#65533;": self-insert
"&#65533;": self-insert
"&#65533;": self-insert
"&#65533;": self-insert
"&#65533;": self-insert
"&#65533;": self-insert
"&#65533;": self-insert
"&#65533;": self-insert
"&#65533;": self-insert
"&#65533;": self-insert
"&#65533;": self-insert
"&#65533;": self-insert
"&#65533;": self-insert
"&#65533;": self-insert
"&#65533;": self-insert
"&#65533;": self-insert
"&#65533;": self-insert
"&#65533;": self-insert
"&#65533;": self-insert
"&#65533;": self-insert
"&#65533;": self-insert
"&#65533;": self-insert
"&#65533;": self-insert
"&#65533;": self-insert
"&#65533;": self-insert
"&#65533;": self-insert
"&#65533;": self-insert
"&#65533;": self-insert
"&#65533;": self-insert
"&#65533;": self-insert
"&#65533;": self-insert
"&#65533;": self-insert
"&#65533;": self-insert
"&#65533;": self-insert
"&#65533;": self-insert
"&#65533;": self-insert
"&#65533;": self-insert
"&#65533;": self-insert
"&#65533;": self-insert
"&#65533;": self-insert
"&#65533;": self-insert
"&#65533;": self-insert
"&#65533;": self-insert
"&#65533;": self-insert
"&#65533;": self-insert
"&#65533;": self-insert
"&#65533;": self-insert
"&#65533;": self-insert
"&#65533;": self-insert
"&#65533;": self-insert
"&#65533;": self-insert
"&#65533;": self-insert
"&#65533;": self-insert
"&#65533;": self-insert
"&#65533;": self-insert
"&#65533;": self-insert
"&#65533;": self-insert
"&#65533;": self-insert
# set-mark (not bound)
# shell-backward-kill-word (not bound)
# shell-backward-word (not bound)
# shell-expand-line (not bound)
# shell-forward-word (not bound)
# shell-kill-word (not bound)
# skip-csi-sequence (not bound)
# start-kbd-macro (not bound)
# tab-insert (not bound)
# tilde-expand (not bound)
"\C-t": transpose-chars
# transpose-words (not bound)
# tty-status (not bound)
# undo (not bound)
# universal-argument (not bound)
# unix-filename-rubout (not bound)
"\C-u": unix-line-discard
"\C-w": unix-word-rubout
# upcase-word (not bound)
# vi-append-eol (not bound)
# vi-append-mode (not bound)
# vi-arg-digit (not bound)
# vi-back-to-indent (not bound)
# vi-bword (not bound)
# vi-bWord (not bound)
# vi-change-case (not bound)
# vi-change-char (not bound)
# vi-change-to (not bound)
# vi-char-search (not bound)
# vi-column (not bound)
# vi-complete (not bound)
# vi-delete (not bound)
# vi-delete-to (not bound)
# vi-editing-mode (not bound)
# vi-end-word (not bound)
"\C-d": vi-eof-maybe
# vi-eword (not bound)
# vi-eWord (not bound)
# vi-fetch-history (not bound)
# vi-first-print (not bound)
# vi-fword (not bound)
# vi-fWord (not bound)
# vi-goto-mark (not bound)
# vi-insert-beg (not bound)
# vi-insertion-mode (not bound)
# vi-match (not bound)
"\e": vi-movement-mode
# vi-next-word (not bound)
# vi-overstrike (not bound)
# vi-overstrike-delete (not bound)
# vi-prev-word (not bound)
# vi-put (not bound)
# vi-redo (not bound)
# vi-replace (not bound)
# vi-rubout (not bound)
# vi-search (not bound)
# vi-search-again (not bound)
# vi-set-mark (not bound)
# vi-subst (not bound)
# vi-tilde-expand (not bound)
# vi-yank-arg (not bound)
# vi-yank-to (not bound)
"\C-y": yank
# yank-last-arg (not bound)
# yank-nth-arg (not bound)
# yank-pop (not bound)

---

### Post by chopinhauer on 2010-08-07
> **Folk Theory said:**
> 
"\C-a": self-insert
"\C-b": self-insert
"\C-c": self-insert
"\C-e": self-insert
"\C-f": self-insert
"\C-g": self-insert
"\C-k": self-insert
"\C-l": self-insert
"\C-o": self-insert
"\C-q": self-insert
"\C-x": self-insert
"\C-z": self-insert
"\C-\\": self-insert
"\C-]": self-insert
"\C-^": self-insert


Did you modify your ~/.inputrc and /etc/inputrc files? On a standard Ubuntu installation the first doesn't exist, while the second contains:
```

# /etc/inputrc - global inputrc for libreadline
# See readline(3readline) and `info rluserman' for more information.

# Be 8 bit clean.
set input-meta on
set output-meta on

# To allow the use of 8bit-characters like the german umlauts, uncomment
# the line below. However this makes the meta key not work as a meta key,
# which is annoying to those which don't need to type in 8-bit characters.

# set convert-meta off

# try to enable the application keypad when it is called.  Some systems
# need this to enable the arrow keys.
# set enable-keypad on

# see /usr/share/doc/bash/inputrc.arrows for other codes of arrow keys

# do not bell on tab-completion
# set bell-style none
# set bell-style visible

# some defaults / modifications for the emacs mode
$if mode=emacs

# allow the use of the Home/End keys
"\e[1~": beginning-of-line
"\e[4~": end-of-line

# allow the use of the Delete/Insert keys
"\e[3~": delete-char
"\e[2~": quoted-insert

# mappings for "page up" and "page down" to step to the beginning/end
# of the history
# "\e[5~": beginning-of-history
# "\e[6~": end-of-history

# alternate mappings for "page up" and "page down" to search the history
# "\e[5~": history-search-backward
# "\e[6~": history-search-forward

# mappings for Ctrl-left-arrow and Ctrl-right-arrow for word moving
"\e[1;5C": forward-word
"\e[1;5D": backward-word
"\e[5C": forward-word
"\e[5D": backward-word
"\e\e[C": forward-word
"\e\e[D": backward-word

$if term=rxvt
"\e[8~": end-of-line
"\eOc": forward-word
"\eOd": backward-word
$endif

# for non RH/Debian xterm, can't hurt for RH/Debian xterm
# "\eOH": beginning-of-line
# "\eOF": end-of-line

# for freebsd console
# "\e[H": beginning-of-line
# "\e[F": end-of-line

$endif

```

---

### Post by Folk Theory on 2010-08-07
I haven't modified them, /etc/inputrc looks like yours, and i don't have .inputrc. what i have done is install

---

### Post by chopinhauer on 2010-08-07
Sorry, I didn't recognize the bindings. They are vi-style bindings. You probably have a
```
set -o vi
```
in your ~/.bashrc .

To revert to Emacs-style bindings type:
```
set -o emacs
```

---

### Post by Folk Theory on 2010-08-07
thank you! that fixed it.

---

### Post by Folk Theory on 2010-08-07
the only one that is still showing is ^C, it still works, but also gets displayed. is there some way to disable that?

---

### Post by itcotbtoemik on 2010-08-07
>'xterm' is the correct value for the terminal type of gnome-terminal

Sorry, but that's never been true, and has been the subject of many
bug-reports.  ncurses provides a "gnome" entry which does match
gnome-terminal.

[http://invisible-island.net/xterm/xterm.faq.html#bug_gnometerm](http://invisible-island.net/xterm/xterm.faq.html#bug_gnometerm)

---

### Post by chopinhauer on 2010-08-07
> **Folk Theory said:**
> the only one that is still showing is ^C, it still works, but also gets displayed. is there some way to disable that?

You can set the option **echo-control-characters** to off in your ~/.inputrc. A
```
echo "set echo-control-characters off" >~/.inputrc
``` and reloading the terminal (or shell) should do it.

It will work when you type CTRL+C on your command line. However the different jobs you run from bash will still output the control character when interrupted.

BTW do you have an explanation how your shell was set to use vi-style bindings?

PS: If you insert a [code\] and [/code\] (without the '\') at the beginning and end of your bindings listing, it will make this thread shorter and more readable.

---

### Post by chopinhauer on 2010-08-07
> **itcotbtoemik said:**
> 
Sorry, but that's never been true, and has been the subject of many
bug-reports.  ncurses provides a "gnome" entry which does match
gnome-terminal.


Thanks for the link, let's say that “xterm” kinda works, but I never noticed how bad a terminal gnome-terminal is.

---

### Post by itcotbtoemik on 2010-08-07
kinda (agree).

Here's some of the bug-reports in gnome-terminal's upstream:

[https://bugzilla.gnome.org/buglist.cgi?quicksearch=xterm](https://bugzilla.gnome.org/buglist.cgi?quicksearch=xterm)
[https://bugzilla.gnome.org/buglist.cgi?query_format=specific&order=relevance+desc&bug_status=__open__&product=vte&content=](https://bugzilla.gnome.org/buglist.cgi?query_format=specific&order=relevance+desc&bug_status=__open__&product=vte&content=)

...although I'm most familiar with the various packagers (Debian, Redhat)

---

### Post by Folk Theory on 2010-08-07
> **chopinhauer said:**
> BTW do you have an explanation how your shell was set to use vi-style bindings?

I use Vim daily at home and at work. I think I read somewhere that setting that value would make it the default editor, which is something I'd want. I didn't realize it would change the bindings to match the editor though.

I really should have recognized the vim bindings...but it just never crossed my mind, not knowing there was such a thing for bash.

Thanks for helping my out, I really appreciate it.

---

### Post by chopinhauer on 2010-08-07
> **Folk Theory said:**
> I use Vim daily at home and at work. I think I read somewhere that setting that value would make it the default editor, which is something I'd want. I didn't realize it would change the bindings to match the editor though.


No, it doesn't change your default editor, just the bash key bindings. Setting your 'EDITOR' variable does that or changing the symlink /usr/bin/editor via the Debian **alternatives** system:
```
sudo update-alternatives --config editor
sudo update-alternatives --config gnome-text-editor
```

---

