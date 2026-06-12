---
title: "View more terminal (terminator) history while in session"
date: 2012-07-17
forum: General Help
---

### Post by babelproofreader on 2012-07-17
I've made a stupid mistake and run an Octave session overnight to produce results to the terminal, with the intention of manually copying and pasting the terminal output to a file. However, I now find that I can't scroll far enough back to copy all the session output. What can I do to access the current session history that is not observable in the terminal window? An added complication is that the terminal I'm using is terminator and there doesn't seem to be an edit option, so edit -> select all -> copy is not available to me. As I write this, the terminal and Octave session are still open, and I need to view the earlier history without either quitting Octave or closing the terminal.

---

### Post by cortman on 2012-07-17
> **babelproofreader said:**
> I've made a stupid mistake and run an Octave session overnight to produce results to the terminal, with the intention of manually copying and pasting the terminal output to a file. However, I now find that I can't scroll far enough back to copy all the session output. What can I do to access the current session history that is not observable in the terminal window? An added complication is that the terminal I'm using is terminator and there doesn't seem to be an edit option, so edit -> select all -> copy is not available to me. As I write this, the terminal and Octave session are still open, and I need to view the earlier history without either quitting Octave or closing the terminal.

Bash stores your history in a your ~/ folder called .bash_history. Unfortunately this is only a history of what was entered to stdin, and AFAIK there's no way to record stdout. Maybe someone will come along and correct me.

---

