---
title: "XOR two files."
date: 2010-02-10
forum: General Help
---

### Post by undecim on 2010-02-10
I've been looking through the repos and Google for a utility to do this, but haven't been able to find one. I could easily write my own program in C, but I don't want to spend much time on it if it's already been done ("don't reinvent the wheel", etc)

I just need a simple program to output the XOR of two files (or a file and stdin, etc). 

Ideally it would stop at EOF of either input and have the option to output the contents of one input up to EOF of the output. (of course, if there is a simple FOSS app to do this already, I can just add those features myself)

This, would be useful for OTP encryption, swapping the contents of two drives in place without an intermediary storage, and various other XOR magic.

---

### Post by ivan.p on 2010-10-03
I don't know about any program that does it.
I assume you've already searched in the Software Center or in aptitude. Maybe somebody uploaded something useful to a PPA.

Search for it. If you still don't find any, here's a program that does what you want:

```

import qualified Data.ByteString.Lazy as B
import Data.Bits (xor)
import System.Environment (getArgs)

main :: IO()
main = do
 args <- getArgs
 if length args /= 2
  then putStrLn "I need two filenames" 
  else do b1 <- B.readFile (head args)
          b2 <- B.readFile (last args)
          B.putStr $ B.pack $ B.zipWith xor b1 b2

```This program takes two filenames given as arguments and outputs to stdout the xor of both files. If one file is larger than the other, it stops when the shortest has been read.

To compile it, save it in a file (for example, xor.hs), install ghc (the haskell compiler) and run:
```

$ ghc --make xor.hs

```If ghc complains about missing libraries or modules, it'll probably complain about bytestring. In that case, install cabal ([http://haskell.org/cabal/download.html](http://haskell.org/cabal/download.html)) and run:
```

$ cabal update
$ cabal install bytestring

```(you need to add ~/.cabal/bin to your path)

Let me know if you have problems with this. Note that the ghc and bytestring dependencies are only necessary to compile the program. Once it's compiled, you can remove ghc, cabal and ~/.cabal (although haskell is a cool language and I strongly recommend you learn it).

If you haven't found anything and you feel this suites you, I wouldn't mind taking this to the next level: improve the code, add a few command line options, create a .deb and upload it to a PPA. That is, if YOU OR SOMEBODY ELSE HELPS ME (it won't take much effort, but I'm kind of tired of doing these things alone).

Cheers ;)

---

### Post by vgfeit on 2011-12-27
This could help:

```
$ man combine
```[HTML]COMBINE(1)                                                                                    COMBINE(1)

NAME
       combine - combine sets of lines from two files using boolean operations

SYNOPSIS
       combine file1 and file2

       combine file1 not file2

       combine file1 or file2

       combine file1 xor file2

       _ file1 and file2 _

       _ file1 not file2 _

       _ file1 or file2 _

       _ file1 xor file2 _

DESCRIPTION
       combine combines the lines in two files. Depending on the boolean operation specified, the
       contents will be combined in different ways:

       and Outputs lines that are in file1 if they are also present in file2.

       not Outputs lines that are in file1 but not in file2.

       or  Outputs lines that are in file1 or file2.

       xor Outputs lines that are in either file1 or file2, but not in both files.[/HTML]

---

### Post by jwbrase on 2011-12-27
Combine isn't the right program. It includes whole lines in the output according to whether those lines are present in each of the input files and the operation being used. The OP, however, seems to be looking for a program that will bitwise XOR each byte of the first input file with the corresponding byte of the second.

---

