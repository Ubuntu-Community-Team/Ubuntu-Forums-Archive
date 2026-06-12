---
title: "Latex (texlive) issue in Karmic"
date: 2010-06-02
forum: General Help
---

### Post by hvymtlsteve on 2010-06-02
Hi all,
I'm trying to get a template working with texlive in Karmic.

When I try to compile normally, I get errors that it can't find certain .sty files, which are part of the standard packages that get installed
(amsmath.sty, etc... graphics.sty, xspace.sty).

If I run latex with sudo, the problem disappears.
I guess this has something to do with file read permissions.

So I found where all of these files are located and did:

```
sudo chmod -R 777 /usr/share/texmf-texlive/
```

This did not solve the problem. Does anybody happen to know what the issue is here? I have done some searching around and haven't found anything useful that doesn't involve copying all the files somewhere else.

Cheers,

Steve

---

### Post by ad_267 on 2010-06-02
LaTeX probably isn't looking in the right places, although I'm not sure how you can go about fixing this. You could try running "sudo texhash" and "texhash", but I'm not sure why it works for root and not you.

You could also check nothing has messed up your TeX environment variables with "env | grep TEX".

---

### Post by hvymtlsteve on 2010-06-02
Thanks for the reply.

texhash works only with sudo and not without.
After running it, still no luck. The only environment variable is TEXINPUTS, which I set myself to point to a directory I set aside for missing packages.

EDIT-- getting rid of my TEXINPUTS on .bashrc seems to have fixed the problem.

Originally I had added it to deal with some missing packages that I didn't want in my source folder, but now that I have installed the massive beast that is texlive-full none of those packages seem to be missing anyway. Oops.

Good call, thanks :)

---

### Post by ad_267 on 2010-06-02
Ok I thought texhash might need to be run as a normal user if you have a ~/texmf.

Hmm well I have a TEXINPUTS set too but it hasn't caused any problems. The line in my .bashrc looks like:

export TEXINPUTS=.:$HOME/uni/phd/thesis/texinputs:

Leaving off the trailing : seems to cause problems similar to what you're describing.

---

