---
title: "Unable to install LaTeX - no pdflatex file in repos"
date: 2010-08-03
forum: General Help
---

### Post by runbei on 2010-08-03
When I install the texlive packages (LaTeX installation) in Mint 9 (= Ubuntu 10.04), the pdflatex module is not installed. Yet it's required for producing pdf files from LaTeX editors, for example jEdit with the LaTeX Tools plug-in. pdflatex is not in the Mint/Ubuntu repos. Has anyone worked around this?

---

### Post by luigi_mb on 2010-08-03
> **runbei said:**
> When I install the texlive packages (LaTeX installation) in Mint 9 (= Ubuntu 10.04), the pdflatex module is not installed. Yet it's required for producing pdf files from LaTeX editors, for example jEdit with the LaTeX Tools plug-in. pdflatex is not in the Mint/Ubuntu repos. Has anyone worked around this?

Did you install texlive-base and textlive-base-latex ?

/luigi

---

### Post by chopinhauer on 2010-08-03
The 'pdflatex' executable is in the **texlive-latex-base** package, but **texlive-full** may interest you as well.

---

### Post by runbei on 2010-08-04
Thanks for the responses. I do have texlive-base and textlive-base-latex installed.

Can you tell me the default compile command for texlive? I think that may be what I've been entering wrong. Thanks.

FOLLOWUP => : I entered "pdflatex" as the compile command, and the jEdit LaTeX Tools plugin is now working. Thanks again for your help. Will mark this solved.

---

