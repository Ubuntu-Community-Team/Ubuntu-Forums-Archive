---
title: "Help on Using Kate text editor"
date: 2011-08-04
forum: General Help
---

### Post by cddpys on 2011-08-04
Hi,

I would like to start using kate to write c++ programs but  kate i am not sure how to go about  actually running the code.  Right now i just have a simple Hello World script. How would i now run this and see an output on the konsole?

thanks for the help!

---

### Post by haresear on 2011-08-04
Is it a script or is it c++ code?

If it is c++ code:
1. Save the code to a file, e.g. "hello.cpp".
2. Compile the code to get an executable file,
   > g++ -o hello hello.cpp
3. Execute the compiled output file,
   > ./hello

If it is a script:
1. Save the script to a file, e.g. "hello.sh"
2. Make the file executable,
   > chmod +x hello.sh
3. Execute the script,
   > ./hello.sh

---

### Post by cddpys on 2011-08-04
Awsome thanks! 

Just what i was looking for.

---

