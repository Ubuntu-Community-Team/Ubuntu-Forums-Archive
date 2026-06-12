---
title: "problem with meschach library"
date: 2011-08-25
forum: General Help
---

### Post by b-612 on 2011-08-25
Hi

I've been using the meschach library for LU decomposition, I have a C project in Eclipse that works fine with the gcc compiler. The thing is that  when I try to compile the same code with the intel compiler (icc) I get an error. This happen when I try to access  allocated memory for the MAT * structure. 

For example:

    MAT * A = m_get(5, 5);
     A->me[2][2] = 3; //SEGMENTATION FAULT

Whenever I try to access some value I get a Segmentation Fault. I already checked that m_get return a valid memory address. The strange thing is that this problem doesn't happen with vectors (VEC *).

Any suggestions ???

---

