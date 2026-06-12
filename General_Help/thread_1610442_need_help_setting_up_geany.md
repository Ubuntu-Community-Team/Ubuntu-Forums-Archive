---
title: "need help setting up geany"
date: 2010-10-31
forum: General Help
---

### Post by camiloorozco on 2010-10-31
i am trying to set u geany on ubuntu 10.04 and i download the linux java jdk from the internet but when i try and make the path i cant select it.

Any ideas why and how i can fix it?

i would appreciate any help

---

### Post by sohlinux on 2010-10-31
> **camiloorozco said:**
> i am trying to set u geany on ubuntu 10.04 and i download the linux java jdk from the internet but when i try and make the path i cant select it.

Any ideas why and how i can fix it?

i would appreciate any help

did you try running it as root? because if its not allowing you to select a path that sounds like the reason

---

### Post by gordintoronto on 2010-10-31
You would save yourself a lot of grief by installing things from Synaptic Package Manager instead of from the Internet.  You're using Windows methods on a Linux system...

---

### Post by camiloorozco on 2010-11-01
how do you run it as a root, 

and ill try downloading from the synaptic package manager

---

### Post by camiloorozco on 2010-11-01
i downloaded it using the synaptic manager thing and on geany i found the file selected it and applied the changes but the compile button is still blacked out. Maybe i selected the wrong file but im not sure whats happening

---

### Post by lykeion on 2010-11-01
Geany > Build > Set Includes and Arguments
Compile: javac "%f"
Execute: java "%e"

Create a java file and save it, and you should be able to compile [F8] and run it [F5]

---

### Post by camiloorozco on 2010-11-01
> **lykeion said:**
> Geany > Build > Set Includes and Arguments
Compile: javac "%f"
Execute: java "%e"

Create a java file and save it, and you should be able to compile [F8] and run it [F5]

i cant select set include and arguments

---

### Post by lykeion on 2010-11-01
How do you mean can't select?
In Geany select Build from menu, then select Set Includes and Arguments. See attached image.
Then just enter the commands in the Compile and Execute textfields.

---

### Post by camiloorozco on 2010-11-01
i cant select it, it doesnt get highlighted when slide my mouse over .

---

### Post by lykeion on 2010-11-01
Do you mean that the Build menu item is disabled?
If so, you have to have a java file in Geany to be able to build.

1. Start with create a new file
File > New

2. Paste this code:
[PHP]public class Hello {
	public static void main(String[] args) {
		System.out.println("Hello world!");
	}
}[/PHP]

3. Save as Hello.java

Now you have a java file to build.

---

### Post by camiloorozco on 2010-11-01
i already had a file to compile but i need help setting up the jdk so that it is actualy possible to write programs.

---

### Post by lykeion on 2010-11-01
Ok, so the problem is installing Java JDK, not compiling Java with Geany like the thread says.

Like previous poster mentioned, don't install by downloading from the web (a.k.a Windows-behavior). 
Ubuntu has a package manager for this: 
*Applications Menu > Ubuntu Software Center*
or for more control use Synaptic:
[I]System > Administration > Synaptic Package Manager
[/I]
Search for "openjdk jdk" to find the package to install Java JDK.
Then you should be able to compile with javac and run with java.

After this, do you still have the problem with Build menu option being disabled in Geany?

---

### Post by camiloorozco on 2010-11-01
i installed the jdk like you said but the menu is still disabled, dont i have to somehow link the jdk and geany together?

---

### Post by lykeion on 2010-11-02
No you don't need to link JDK and Geany, more than to enter javac and java in Build > Set Includes and Arguments like explained in previous post.
However it's strange that the Compile/Execute is disabled in the Build menu. 

1. Could you tell me your Geany version (Geany > Help > About). It should display something like "Geany 0.18" at the top.

2. Make sure that the filename of the Java source file ends with .java

3. And after loading your java file in Geany, make sure it parses it as a Java source file. (Geany > Document > Set Filetype > Programming Languages > Java source file)

---

