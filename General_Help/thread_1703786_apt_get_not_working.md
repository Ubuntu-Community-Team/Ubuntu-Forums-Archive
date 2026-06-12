---
title: "apt get not working"
date: 2011-03-09
forum: General Help
---

### Post by rcschmie on 2011-03-09
Ubuntu 10.10; after a good install and good update, apt-get quit working.  Unable to install new programs, error note says there is a programming error in aptdaemon.  When I try to update apt-get, error messages state"could not lock /var/lib/dpkg/lock - open resource temporarily unavailable" and "unable to lock the administration directory (/var/lib/dpkg/), is another process using it?"

Also during updates, an install of mscore fonts presents a grey screen EULA with an OK at the bottom, that blanks the terminal window.  No keystroke clears this screen and closing the terminal says there was a process running, even though the window persists after a long interim and there can't be any process running.

---

### Post by Don Barzini on 2011-03-09
> **rcschmie said:**
> Ubuntu 10.10; after a good install and good update, apt-get quit working.  Unable to install new programs, error note says there is a programming error in aptdaemon.  When I try to update apt-get, error messages state"could not lock /var/lib/dpkg/lock - open resource temporarily unavailable" and "unable to lock the administration directory (/var/lib/dpkg/), is another process using it?"

Also during updates, an install of mscore fonts presents a grey screen EULA with an OK at the bottom, that blanks the terminal window.  No keystroke clears this screen and closing the terminal says there was a process running, even though the window persists after a long interim and there can't be any process running.

Do you have the Synaptic Package Manager open when you are trying to use apt-get in a terminal window?

If so, you must close Synaptic to use apt-get in a terminal. The system won't allow multiple instances of that process.

---

### Post by oldos2er on 2011-03-09
> **rcschmie said:**
> Also during updates, an install of mscore fonts presents a grey screen EULA with an OK at the bottom, that blanks the terminal window.  No keystroke clears this screen and closing the terminal says there was a process running, even though the window persists after a long interim and there can't be any process running.

Run **sudo dpkg --configure -a**, when the EULA comes up again, use Tab to highlight OK then press Enter.

---

### Post by rcschmie on 2011-03-10
> **Don Barzini said:**
> Do you have the Synaptic Package Manager open when you are trying to use apt-get in a terminal window?

If so, you must close Synaptic to use apt-get in a terminal. The system won't allow multiple instances of that process.
Thank you for your fast response. the two processes were not open concurrently.  Failing to be able to clear the problem, I reinstalled linux.

---

### Post by rcschmie on 2011-03-10
> **oldos2er said:**
> Run **sudo dpkg --configure -a**, when the EULA comes up again, use Tab to highlight OK then press Enter.
Thanks for the response.  The grey screen covers the terminal window so that I cant see it to enter anything. Hopefully the problem will not happen again after reinstall.

---

### Post by oldos2er on 2011-03-10
> **rcschmie said:**
> Thanks for the response.  The grey screen covers the terminal window so that I cant see it to enter anything. Hopefully the problem will not happen again after reinstall.

You may need to use the space bar to page down to the 'OK'.

---

