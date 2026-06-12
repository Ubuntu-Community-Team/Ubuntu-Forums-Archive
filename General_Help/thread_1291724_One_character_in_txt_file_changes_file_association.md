---
title: "One character in txt file changes file association"
date: 2009-10-15
forum: General Help
---

### Post by Ctulhu on 2009-10-15
I have a strange issue with a text file. This text file contains code in the R programming language. The intended version of this file contains the following line of code

# graph 1, based on percentages

When I save this file, the file icon changes and its file type gets changes to "Graphviz DOT graph (text/vnd.graphviz)". But when I take the very same file and change just one character in this line to

# graph_1, based on percentages

then its file icon changes again and it becomes a regular text file. What the heck is that and how can I not have that happen?
C

---

### Post by P4man on 2009-10-15
is it the first line of the file?
You could add a shebang line for R, though I have no idea what it would have to be. Something like

#!/usr/local/your_R_interpreter

---

### Post by StuartN on 2009-10-15
> **P4man said:**
> You could add a shebang line for R

Out of interest, from where does Bash determine that "# graph" is to be interpreted by "Graphviz DOT graph (text/vnd.graphviz)"?

The R system is located at /usr/bin/R, or you can check with the command **which R**, so the shebang would be #!/usr/bin/R, but is it possible to include R options, e.g. #!/usr/bin/R --vanilla --gui X11 ?

---

### Post by P4man on 2009-10-15
> **StuartN said:**
> Out of interest, from where does Bash determine that "# graph" is to be interpreted by "Graphviz DOT graph (text/vnd.graphviz)"?

The R system is located at /usr/bin/R, or you can check with the command **which R**, so the shebang would be #!/usr/bin/R, but is it possible to include R options, e.g. #!/usr/bin/R --vanilla --gui X11 ?

No idea. But I don't think its bash, its nautilus that interpretes it I think.

---

### Post by Ctulhu on 2009-10-15
No, it's not the first line of this file, it's line 12. Here's the whole file:

-------------------------------
&#65279;rm(list=ls(all=T))
library(R.utils)

setwd("XXX")

# load files
load("15m_chx_x50_FINAL.RData")

attach(x.50)

# new SIO vs. CDE graphs, based on x.50
# graph_1, based on percentages
sio.x.perc <- X_FREQ_SIO/(BOTH_FREQ_SIO) # percentages of the x form in SIO
cde.x.perc <- X_FREQ_CDE/(BOTH_FREQ_CE)  # percentages of the x form in CDE
joint.freq <- log(BOTH_FREQ_SIO+BOTH_FREQ_CE) # joint frequency of words in both SIO and CDE

# graph 2, based on logs of percentages
sio.x.perc.log <- log(sio.x.perc*100+1) # log of the percentages (+1)
cde.x.perc.log <- log(cde.x.perc*100+1) # log of the percentages (+1)

jpeg("15o_percgraph_chx.jpg", width=900, height=677, quality=100)
plot(mean(sio.x.perc.log)~mean(joint.freq), xlim=c(4.5, 10), ylim=c(0, 4.7), xlab="Log word frequency in both corpora", ylab="Log percentage of x forms", type="n", axes=F) # note: different ylim
   grid(); axis(1);  axis(2, at=seq(0, 4.5, 0.5), labels=round(exp(seq(0, 4.5, 0.5)), 0))
   points(joint.freq, cde.x.perc.log, pch=5, col="grey20")
   text(joint.freq, sio.x.perc.log, labels=FORM, font=3, cex=0.925, srt=45)
   segments(joint.freq, sio.x.perc.log, joint.freq, cde.x.perc.log, col=ifelse(sio.x.perc.log>cde.x.perc.log, "darkgrey", "blue"), lty=2)
dev.off()
png2("15o_percgraph_chx.png", width=1800, height=1354, res=300)
plot(mean(sio.x.perc.log)~mean(joint.freq), xlim=c(4.5, 10), ylim=c(0, 4.7), xlab="Log word frequency in both corpora", ylab="Log percentage of x forms", type="n", axes=F) # note: different ylim
   grid(); axis(1);  axis(2, at=seq(0, 4.5, 0.5), labels=round(exp(seq(0, 4.5, 0.5)), 0))
   points(joint.freq, cde.x.perc.log, pch=5, col="grey20")
   text(joint.freq, sio.x.perc.log, labels=FORM, font=3, cex=0.925, srt=45)
   segments(joint.freq, sio.x.perc.log, joint.freq, cde.x.perc.log, col=ifelse(sio.x.perc.log>cde.x.perc.log, "darkgrey", "blue"), lty=2)
dev.off()
-------------------------------

But that's a bug, right?!

---

### Post by P4man on 2009-10-15
FWIW, I can't reproduce the issue on karmic (beta). I put that script in a file, and regardless if I change line 12 to  graph 1 or graph_1, its always seen as a text file.

---

