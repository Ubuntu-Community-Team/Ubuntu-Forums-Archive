---
title: "help with java"
date: 2011-09-24
forum: General Help
---

### Post by totalnewbsood on 2011-09-24
Hi everyone

I am new to ubuntu, programming and java and require a bit of help. I recently started a programming course and they have started us on java. i'm using the eclipse java editor but can not import the format IO which should let me read from and to files, use strings and all the rest of the beginner stuff. I have copied and pasted the folder into the class folder but it still does not recognise the import. 

import FormatIO.*;


public class PracEx2 {
 public static void main(String[] args)
   {
      System.out.println("Hello world");
      
      Console con = new Console;
      con.println("Hello, World!");


This basic program does not work. Is there a way that I can perform all of the functions i need to? I understand that this is not very clear so please message me if you think you can help or ask a few questions

cheers

---

### Post by Linux_junkie on 2011-09-24
I don't think your import command is valid. Try 

import java.io.*;

It might be a good idea for you to bookmark this [link]("http://download.oracle.com/javase/6/docs/api/")

---

