---
title: "Problem with SWI-Prolog built-in editor (PceEmacs) in Jaunty (9.04)."
date: 2009-10-22
forum: General Help
---

### Post by VectorZero on 2009-10-22
Hi! Not sure this is the best place for this post, but could not figure out a better one.

I'm using SWI-Prolog for a while, but since I upgraded to Jaunty (9.04) I'm having problems to use the built-in editor (PceEmacs). Every time I try to load the editor I get an ugly error message.

```
xxx@xxxxx:~$ xpce
XPCE 6.6.58, July 2008 for i386-linux-gnu and X11R6
Copyright (C) 1993-2007 University of Amsterdam.
XPCE comes with ABSOLUTELY NO WARRANTY. This is free software,
and you are welcome to redistribute it under certain conditions.
The host-language is SWI-Prolog version 5.6.59

For HELP on prolog, please type help. or apropos(topic).
         on xpce, please type manpce.

?- emacs.
[PCE fatal: @pce/pce: Signal trapped: Floating point exception
	in: 	<No exception goal>
]
	[ 8] M @4948327/editor ->initialise(@default/constant, 40, 8, @default/constant)
	[ 7] M @4945970/view <-create_editor(@4945388/size)
	[ 6] M @4945970/view ->initialise(@default/constant, @4945388/size, @default/constant, @default/constant)
	[ 5] M @emacs_mark_list/emacs_bookmark_editor ->initialise()
	[ 4] 
	[ 3] M @emacs/emacs ->initialise(@emacs_buffers/dict)
	[ 2] 
	[ 1] M @prolog/host ->call(trap_ref, emacs)
Host stack:
     [15] send(new(_G2122, view(size:=size(40, 8))), below(@4901835/dialog))
     [14] Send-method on @emacs_mark_list/emacs_bookmark_editor: emacs_bookmark_editor->initialise
    <Alien goal>
     [13] new(@emacs_mark_list/emacs_bookmark_editor, emacs_bookmark_editor)
     [12] Send-method on @emacs/emacs: emacs->initialise(@emacs_buffers/dict)
    <Alien goal>
     [11] new(@emacs/emacs, start_emacs:emacs(@emacs_buffers/dict))
ERROR: :- pce_global/2: create failed: emacs(@emacs_buffers)
ERROR: pce(object) `@emacs' does not exist
^  Exception: (9) send(@emacs, start) ?
```

I have already Googled it for a solution but could not find one.

I would greatly appreciate if anybody could help me with that. (As a work around I'm using gedit to edit the code, but it is not what I would like to to.)

Thanks in advance.

---

### Post by VectorZero on 2009-10-24
Hi guys! Would **REALLY** appreciate some help with this matter. Thanks.

---

### Post by blwizard on 2009-10-24
Not sure about your problem, the editor loads up fine on my 9.04. But I usually use vim for prolog file editing, need to set the syntax highlighting manually however.

Try running it as root and see if the problem still exists. sometime I can't run some programs because some file permissions are magically changed without me noticing.

---

