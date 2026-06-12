---
title: "Process problem in java"
date: 2009-09-28
forum: General Help
---

### Post by Vishnu V on 2009-09-28
Hai 
I am beginner in programming and now 
i am trying to run xwinwrap through a java pgm
Here is the important part
```

import java.io.*;
class Video
{
	private static String name =null;
	public static void main(String[] arg)
	{
		execute("zenity --file-selection"); //choose a file 
		execute("xwinwrap  -ni -o 0.6 -fs -s -st -sp -b -nf -o 0.75 -- mplayer -wid WID "+name);
	}
	public static void execute(String cmd)
	{
		try
		{
		Process P = Runtime.getRuntime().exec(cmd);
		P.waitFor();
		BufferedReader br = new BufferedReader(new InputStreamReader(P.getInputStream()));
		name= br.readLine();
		}
		catch(Exception i)
		{
			System.out.println("Exception "+i);
		}
	}
}

```
the problem is that I cannot play videos which have space in their name(" ")
i tried this too 
```
name = name.replace(" ","\\ ");
```

What is the problem here ?
please help

Thanks in Advance

---

### Post by Joshka89 on 2009-09-28
What happens when you attempt to play the videos? DOes it give you an error? If so tell us what it is

---

### Post by Vishnu.V on 2009-09-28
It doesnot show any error

---

### Post by Joshka89 on 2009-09-28
try to change your
```
name = name.replace(" ","\\ ");
```line to:

```
name = name.replace(" ","#");
```the \\ may be another unreadable character.
Or if # also does not work, change it to something less likely to have confliction due to symbols, like &, -, or (.  

Let me know if that helps

---

### Post by Vishnu V on 2009-09-28
> try to change your
Code:

name = name.replace(" ","\\ ");

line to:

Code:

name = name.replace(" ","#");

the \\ may be another unreadable character.
Or if # also does not work, change it to something less likely to have confliction due to symbols, like &, -, or (.

Let me know if that helps
Sorry
that too fails

---

### Post by diafanos on 2009-09-28
> **Joshka89 said:**
> try to change your
```
name = name.replace(" ","\\ ");
```line to:

```
name = name.replace(" ","#");
```the \\ may be another unreadable character.
Or if # also does not work, change it to something less likely to have confliction due to symbols, like &, -, or (.  

Let me know if that helps


Using this way, you just change the name of the file. 
E.g. a file named "The sun.avi" will be changed to "The#sun.avi"
No chance to work!

@Joshka89

What's the outcome of the 
```

System.out.println(name);

```
before and after ```
name = name.replace(" ","\\ ");
``` command?

---

### Post by Vishnu V on 2009-09-28
Outcome of System.out.println(name)
before name = name.replace(" ","\\ ");
```
/media/storage/Videos/windows vs ubuntu.mp4
```
after
```
/media/storage/Videos/windows\ vs\ ubuntu.mp4
```

---

### Post by diafanos on 2009-09-29
try the following code:
```

import java.io.*;
class Video
{
	private static String name =null;
	public static void main(String[] arg)
	{
	
		String[] selectFileArgs = {"zenity", "--file-selection"};
		execute(selectFileArgs); //choose a file 
		String[] executeCommandArgs = {"xwinwrap  -ni -o 0.6 -fs -s -st -sp -b -nf -o 0.75 -- mplayer -wid WID", name};
		execute(executeCommandArgs); //execute program
		
	}
	public static void execute(String[] cmd)
	{
		try
		{
		Process P = Runtime.getRuntime().exec(cmd);
		P.waitFor();
		BufferedReader br = new BufferedReader(new InputStreamReader(P.getInputStream()));
		name= br.readLine();
		}
		catch(Exception i)
		{
			System.out.println("Exception "+i);
		}
	}
}


```

because ***exec(String command)*** breaks the command into command line arguments at whitespace characters (even if you use escape characters)
and executes the ***exec(String[] commands)***.

So, in order to override this behaviour you need to call the later command when there is whitespace involved.

I don't have your *xwinwrap* program, so I couldn't test it by myself, but I think it will be fine now.

---

### Post by Vishnu V on 2009-10-01
Sorry for the late response

Now i got an exception that
```

Exception java.io.IOException: Cannot run program "xwinwrap  -ni -o 0.6 -fs -s -st -sp -b -nf -o 0.75 -- mplayer -wid WID ": java.io.IOException: error=2, No such file or directory

```

---

### Post by diafanos on 2009-10-16
Replace this command:

```

String[] executeCommandArgs = {"xwinwrap  -ni -o 0.6 -fs -s -st -sp -b -nf -o 0.75 -- mplayer -wid WID", name};

```


with that:

```

String[] executeCommandArgs = {"xwinwrap", "-ni", "-o", "0.6", "-fs", "-s", "-st", "-sp", "-b", "-nf", "-o", "0.75", "--", "mplayer", "-wid", "WID", name};

```

---

### Post by Vishnu V on 2009-10-17
Thanks a lot.
problem solved

---

