---
title: "Command Link"
date: 2011-07-14
forum: General Help
---

### Post by disconnectus on 2011-07-14
Hello, 

To compile a simple program on an LLNL x86_64-linux system where libunwind is installed, add the following libraries to your link command:

    -L${mpiP_root}/lib -lmpiP -lm -lbfd -liberty -lunwind

What is a Link Command and how can we add a library to it. 

I have searched it in web but couldn´t find anything. 

Thanks

---

