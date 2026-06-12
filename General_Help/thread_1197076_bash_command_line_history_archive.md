---
title: "bash command line history archive"
date: 2009-06-25
forum: General Help
---

### Post by supradave on 2009-06-25
I have a little addition to my .bashrc that sends every command I type in to an archive.  I like to be able to keep track of things that I have written in the past.  What I'm wondering is if there's a way to have the script add only real commands.  For example, how many times have I typed in 'l s-l' rather than 'ls -l'?  For obvious reasons, I don't really need to save those types of mistakes.

By adding the following lines:  

#unset time stamping.  Uses the date command formats (man date)
#If you wanted to set it 'export HISTTIMEFORMAT="%s "
unset HISTTIMEFORMAT

#if the above is unset, the commands start at the 8th column.
#otherwise, you'd get the history number, which would hover
#around 500.  Unnecessary info.  Of course, if you have date/time
#info, you'll have to change the cut command.
PROMPT_COMMAND="${PROMPT_COMMAND:+$PROMPT_COMMAND ; }"'echo "$(history 1 | /usr/bin/cut -c8-)" >> ${HISTFILE}.archive'
#If that smiley is there, that's '- c 8 -' without the spaces.

I'm torn between the failed command and the non-existent command.  If anyone has a solution to either, I'd appreciate it.

Thanks,
Dave

---

### Post by lovinglinux on 2009-06-25
You should put code inside the code tag:

```

PROMPT_COMMAND="${PROMPT_COMMAND:+$PROMPT_COMMAND ; }"'echo "$(history 1 | /usr/bin/cut -c8-)" >> ${HISTFILE}.archive'

```

It won't convert the smiley and makes easier to read large amounts of code.

---

