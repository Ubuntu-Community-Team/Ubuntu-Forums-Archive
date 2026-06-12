---
title: "recalling backrounded processes?"
date: 2005-03-12
forum: General Help
---

### Post by epehekt on 2005-03-12
When I background BitchX, for example,  with CTRL-Z, how do I bring that process back up to use it?   I'd like to be able to stay connected in the background.

---

### Post by WW on 2005-03-12
fg

---

### Post by epehekt on 2005-03-13
Thanks!  

Maybe someone can tell me how to keep the process open after quiting/logging out.  I get "Processes stopped" when I try to logout, and they end up dying.

Just for clarification, I'd like to leave my opped nick logged in on a channel, so I can ssh from anywhere to use it.

---

### Post by ssam on 2005-03-13
Have a look at [cli magic : background forground suspend](http://docs.linux.com/article.pl?sid=04/03/06/1519208&tid=89&tid=14) , it describes ctrl-z, fg, bg and jobs.

---

### Post by WakkiTabakki on 2005-03-13
Try running your commad with nohup (NO Hang UP)

Wakki@Linux:~ $  nohup command &


/N

---

### Post by epehekt on 2005-03-13
Thanks to everyone who replied, I not have my problem solved.  8-)

---

### Post by ssam on 2005-03-14
may be you can do this with screen. i am not sure as i have not used it.

---

### Post by zyiro on 2005-06-08
the easiest way to do this is to use the /detach command it will bring you back to a shell then to get back into bitchx from any screen type scr-bx.


-Garrett

---

