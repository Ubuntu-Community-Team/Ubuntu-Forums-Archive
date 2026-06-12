---
title: "Turned java to scrambled eggs, need help."
date: 2010-08-24
forum: General Help
---

### Post by jackechanprime on 2010-08-24
Hi again all, a few of you might remember that i've been having problems with getting java apps running, if you remember me at all, which i doubt. Well, in my tinkering i seem to have created a total mess and as usual need a little help getting myself out of it.

The reason behind this one is i need to get a program running for college that runs in java, it's directly related to my Math course, namely it's the homework. Without this program running, i'm screwed, and out about 2-grand for tuition.

So i REALLY need help getting java and this program running, and soon. It's probably best to simply purge all forms and/or variants of java from the system (and i'm pretty sure i've tried to install every type of java out there) and start fresh. Especially since i've got java folders coming out my computers ears because of all the things i've been trying get it working.

at the end of the day i simply need this command sequence to get a java plugin working properly:

Open a terminal and type: (adapt the directory to your own Java VM lib/ext directory)

> su root
Password: (Type in the root password)
> cp aleksPack10.jar /usr/java/{{j2re1.4.1}}/lib/ext/
> exit

{{this file}} is where i'm having trouble, A) because i've got something like 40 similar files all over my system, and have nooooo idea which one of them (or which combination of them, god forbid) is actually functional. and B) because I'm using (or trying to) Jre6, so that's not even the right file version. I have "alekspack10.jar" sitting on my desktop at the moment, which is an apparently an archive of all the plugin's system files and (i'm guessing here) simply needs to be plopped down in the right directory and made functional.

help?:(
~Q

---

### Post by spjackson on 2010-08-24
Open a terminal and type
```
java -verbose -version
```This will tell you, for the default java executable in your path, the default classpaths that are loaded. For example, on my system this would be

/usr/lib/jvm/java-6-openjdk/jre/lib

so I would use the ext subdirectory within that.

This assumes, of course, that the default java in your path is the java that you are going to use for your task! If not, choose the java that you are going to use and do the same thing with that instead.

Hope this helps.

---

### Post by GregBrannon on 2010-08-24
Just a suggestion:

Get *something* for the $2K you're paying for this course, and ask the instructor for help.

What you're trying to do isn't that hard.  Helping you with it is risky, because you've only given us a small piece of the puzzle, AND the small piece we've been given has been filtered by you, someone who apparently doesn't understand the first thing about what they're trying to do.

Again, ask the prof for help.  If there's some reason that's not possible, ask another student, preferably a cute one of the opposite sex.

---

### Post by jackechanprime on 2010-08-24
that should help tons, but there is one snag...

you can do that? Assigning default java or choosing which program to run? i just kinda let firefox run whatever it decided (for whatever reason) looks like it'll work, hence the installing it in all sorts of places until firefox actually found it.

 ...perhaps this would have been a good thing to know a loooooooong time ago.... >_<

i have -no- idea which java is active/default honestly. Whatever firefox is using at the moment (which i dont know) is whatever is working. I don't go in and select which program i want it to use, i just want it to use one that actually functions.

ech... like i said... it's a nasty little hairball i've gotten myself into... ;_; all i wanted to do is get jre6 running in firefox.

well, lets hope this is the right java.

here goes!!!

~Q

---

### Post by oldos2er on 2010-08-24
Which version of Ubuntu are you using? Can you post the output of ```
java -v
``` ?

---

### Post by jackechanprime on 2010-08-24
oh i already did ask the prof. He said contact the company, which i did, and the company gave me the command sequence that i stated in my first post. You guys really dont need to worry about harming my computer, there's not any valuable data on it in the first place.

and erm... just ask and additional "puzzle pieces" will be provided. I'm just really bad with getting plugins working. like i said, i perfer the more dramatic options such as simply purging all types/varients of java from the system and starting from scratch, even so far as nerfing firefox if we need to do that to start at "ground zero."

i'm actually pretty tech savvy, i'm just kinda new at software stuff like this. i've been using my computer as a guinea pig for a while with this java issue. I do have java working, just for the record, "fully functional" however is another story.

ask for what you need, and i'll tell you... just make sure you tell me how to ask my computer the same question... just in case. >_>

---

### Post by jackechanprime on 2010-08-24
I ran that and got this:

jackechan@jackechan-laptop:~$ java -v
Unrecognized option: -v
Could not create the Java virtual machine.
jackechan@jackechan-laptop:~$ 


I ran spjackson's code and got this as an output... O_o not sure if this is a good thing... or a very bad thing....

jackechan@jackechan-laptop:~$ java -verbose -version
[Loaded java.lang.Object from shared objects file]
[Loaded java.io.Serializable from shared objects file]
[Loaded java.lang.Comparable from shared objects file]
[Loaded java.lang.CharSequence from shared objects file]
[Loaded java.lang.String from shared objects file]
[Loaded java.lang.reflect.GenericDeclaration from shared objects file]
[Loaded java.lang.reflect.Type from shared objects file]
[Loaded java.lang.reflect.AnnotatedElement from shared objects file]
[Loaded java.lang.Class from shared objects file]
[Loaded java.lang.Cloneable from shared objects file]
[Loaded java.lang.ClassLoader from shared objects file]
[Loaded java.lang.System from shared objects file]
[Loaded java.lang.Throwable from shared objects file]
[Loaded java.lang.Error from shared objects file]
[Loaded java.lang.ThreadDeath from shared objects file]
[Loaded java.lang.Exception from shared objects file]
[Loaded java.lang.RuntimeException from shared objects file]
[Loaded java.security.ProtectionDomain from shared objects file]
[Loaded java.security.AccessControlContext from shared objects file]
[Loaded java.lang.ClassNotFoundException from shared objects file]
[Loaded java.lang.LinkageError from shared objects file]
[Loaded java.lang.NoClassDefFoundError from shared objects file]
[Loaded java.lang.ClassCastException from shared objects file]
[Loaded java.lang.ArrayStoreException from shared objects file]
[Loaded java.lang.VirtualMachineError from shared objects file]
[Loaded java.lang.OutOfMemoryError from shared objects file]
[Loaded java.lang.StackOverflowError from shared objects file]
[Loaded java.lang.IllegalMonitorStateException from shared objects file]
[Loaded java.lang.ref.Reference from shared objects file]
[Loaded java.lang.ref.SoftReference from shared objects file]
[Loaded java.lang.ref.WeakReference from shared objects file]
[Loaded java.lang.ref.FinalReference from shared objects file]
[Loaded java.lang.ref.PhantomReference from shared objects file]
[Loaded java.lang.ref.Finalizer from shared objects file]
[Loaded java.lang.Runnable from shared objects file]
[Loaded java.lang.Thread from shared objects file]
[Loaded java.lang.Thread$UncaughtExceptionHandler from shared objects file]
[Loaded java.lang.ThreadGroup from shared objects file]
[Loaded java.util.Dictionary from shared objects file]
[Loaded java.util.Map from shared objects file]
[Loaded java.util.Hashtable from shared objects file]
[Loaded java.util.Properties from shared objects file]
[Loaded java.lang.reflect.AccessibleObject from shared objects file]
[Loaded java.lang.reflect.Member from shared objects file]
[Loaded java.lang.reflect.Field from shared objects file]
[Loaded java.lang.reflect.Method from shared objects file]
[Loaded java.lang.reflect.Constructor from shared objects file]
[Loaded sun.reflect.MagicAccessorImpl from shared objects file]
[Loaded sun.reflect.MethodAccessor from shared objects file]
[Loaded sun.reflect.MethodAccessorImpl from shared objects file]
[Loaded sun.reflect.ConstructorAccessor from shared objects file]
[Loaded sun.reflect.ConstructorAccessorImpl from shared objects file]
[Loaded sun.reflect.DelegatingClassLoader from shared objects file]
[Loaded sun.reflect.ConstantPool from shared objects file]
[Loaded sun.reflect.FieldAccessor from shared objects file]
[Loaded sun.reflect.FieldAccessorImpl from shared objects file]
[Loaded sun.reflect.UnsafeFieldAccessorImpl from shared objects file]
[Loaded sun.reflect.UnsafeStaticFieldAccessorImpl from shared objects file]
[Loaded java.lang.Iterable from shared objects file]
[Loaded java.util.Collection from shared objects file]
[Loaded java.util.AbstractCollection from shared objects file]
[Loaded java.util.List from shared objects file]
[Loaded java.util.AbstractList from shared objects file]
[Loaded java.util.RandomAccess from shared objects file]
[Loaded java.util.Vector from shared objects file]
[Loaded java.lang.Appendable from shared objects file]
[Loaded java.lang.AbstractStringBuilder from shared objects file]
[Loaded java.lang.StringBuffer from shared objects file]
[Loaded java.lang.StringBuilder from shared objects file]
[Loaded java.lang.StackTraceElement from shared objects file]
[Loaded java.nio.Buffer from shared objects file]
[Opened /usr/lib/jvm/java-6-openjdk/jre/lib/rt.jar]
[Loaded java.lang.Boolean from shared objects file]
[Loaded java.lang.Character from shared objects file]
[Loaded java.lang.Number from shared objects file]
[Loaded java.lang.Float from shared objects file]
[Loaded java.lang.Double from shared objects file]
[Loaded java.lang.Byte from shared objects file]
[Loaded java.lang.Short from shared objects file]
[Loaded java.lang.Integer from shared objects file]
[Loaded java.lang.Long from shared objects file]
[Loaded java.io.ObjectStreamField from shared objects file]
[Loaded java.util.Comparator from shared objects file]
[Loaded java.lang.String$CaseInsensitiveComparator from shared objects file]
[Loaded java.security.Guard from shared objects file]
[Loaded java.security.Permission from shared objects file]
[Loaded java.security.BasicPermission from shared objects file]
[Loaded java.lang.RuntimePermission from shared objects file]
[Loaded java.util.AbstractMap from shared objects file]
[Loaded sun.misc.SoftCache from shared objects file]
[Loaded java.lang.ref.ReferenceQueue from shared objects file]
[Loaded java.lang.ref.ReferenceQueue$Null from shared objects file]
[Loaded java.lang.ref.ReferenceQueue$Lock from shared objects file]
[Loaded java.util.HashMap from shared objects file]
[Loaded java.lang.annotation.Annotation from shared objects file]
[Loaded java.util.Map$Entry from shared objects file]
[Loaded java.util.HashMap$Entry from shared objects file]
[Loaded java.security.AccessController from shared objects file]
[Loaded java.lang.reflect.ReflectPermission from shared objects file]
[Loaded java.security.PrivilegedAction from shared objects file]
[Loaded sun.reflect.ReflectionFactory$GetReflectionFactoryAction from shared objects file]
[Loaded java.util.Stack from shared objects file]
[Loaded sun.reflect.ReflectionFactory from shared objects file]
[Loaded java.lang.ref.Reference$Lock from shared objects file]
[Loaded java.lang.ref.Reference$ReferenceHandler from shared objects file]
[Loaded java.lang.ref.Finalizer$FinalizerThread from shared objects file]
[Loaded java.util.Hashtable$Entry from shared objects file]
[Loaded java.nio.charset.Charset from shared objects file]
[Loaded java.nio.charset.spi.CharsetProvider from shared objects file]
[Loaded sun.nio.cs.FastCharsetProvider from shared objects file]
[Loaded sun.nio.cs.StandardCharsets from shared objects file]
[Loaded sun.util.PreHashedMap from shared objects file]
[Loaded sun.nio.cs.StandardCharsets$Aliases from shared objects file]
[Loaded sun.nio.cs.StandardCharsets$Classes from shared objects file]
[Loaded sun.nio.cs.StandardCharsets$Cache from shared objects file]
[Loaded java.lang.ThreadLocal from shared objects file]
[Loaded java.util.concurrent.atomic.AtomicInteger from shared objects file]
[Loaded sun.misc.Unsafe from shared objects file]
[Loaded java.lang.IncompatibleClassChangeError from shared objects file]
[Loaded java.lang.NoSuchMethodError from shared objects file]
[Loaded sun.reflect.Reflection from shared objects file]
[Loaded java.lang.Math from shared objects file]
[Loaded java.util.Set from shared objects file]
[Loaded java.util.AbstractSet from shared objects file]
[Loaded java.util.HashMap$EntrySet from shared objects file]
[Loaded java.util.Iterator from shared objects file]
[Loaded java.util.HashMap$HashIterator from shared objects file]
[Loaded java.util.HashMap$EntryIterator from shared objects file]
[Loaded java.lang.Class$3 from shared objects file]
[Loaded java.lang.reflect.Modifier from shared objects file]
[Loaded sun.reflect.LangReflectAccess from shared objects file]
[Loaded java.lang.reflect.ReflectAccess from shared objects file]
[Loaded java.util.Arrays from shared objects file]
[Loaded sun.nio.cs.HistoricallyNamedCharset from shared objects file]
[Loaded sun.nio.cs.Unicode from shared objects file]
[Loaded sun.nio.cs.UTF_8 from shared objects file]
[Loaded java.lang.Class$1 from shared objects file]
[Loaded sun.reflect.ReflectionFactory$1 from shared objects file]
[Loaded sun.reflect.NativeConstructorAccessorImpl from shared objects file]
[Loaded sun.reflect.DelegatingConstructorAccessorImpl from shared objects file]
[Loaded sun.misc.VM from shared objects file]
[Loaded java.lang.StringCoding from shared objects file]
[Loaded java.lang.ThreadLocal$ThreadLocalMap from shared objects file]
[Loaded java.lang.ThreadLocal$ThreadLocalMap$Entry from shared objects file]
[Loaded java.lang.StringCoding$StringDecoder from shared objects file]
[Loaded java.nio.charset.CharsetDecoder from shared objects file]
[Loaded sun.nio.cs.UTF_8$Decoder from shared objects file]
[Loaded java.nio.charset.CodingErrorAction from shared objects file]
[Loaded java.nio.ByteBuffer from shared objects file]
[Loaded java.nio.HeapByteBuffer from shared objects file]
[Loaded java.nio.Bits from shared objects file]
[Loaded java.nio.ByteOrder from shared objects file]
[Loaded java.lang.Readable from shared objects file]
[Loaded java.nio.CharBuffer from shared objects file]
[Loaded java.nio.HeapCharBuffer from shared objects file]
[Loaded java.nio.charset.CoderResult from shared objects file]
[Loaded java.nio.charset.CoderResult$Cache from shared objects file]
[Loaded java.nio.charset.CoderResult$1 from shared objects file]
[Loaded java.nio.charset.CoderResult$2 from shared objects file]
[Loaded sun.misc.Version from shared objects file]
[Loaded java.io.Closeable from shared objects file]
[Loaded java.io.InputStream from shared objects file]
[Loaded java.io.FileInputStream from shared objects file]
[Loaded java.io.FileDescriptor from shared objects file]
[Loaded sun.misc.JavaIOFileDescriptorAccess from /usr/lib/jvm/java-6-openjdk/jre/lib/rt.jar]
[Loaded java.io.FileDescriptor$1 from /usr/lib/jvm/java-6-openjdk/jre/lib/rt.jar]
[Loaded sun.misc.SharedSecrets from shared objects file]
[Loaded java.io.Flushable from shared objects file]
[Loaded java.io.OutputStream from shared objects file]
[Loaded java.io.FileOutputStream from shared objects file]
[Loaded java.io.FilterInputStream from shared objects file]
[Loaded java.io.BufferedInputStream from shared objects file]
[Loaded java.util.concurrent.atomic.AtomicReferenceFieldUpdater from shared objects file]
[Loaded java.util.concurrent.atomic.AtomicReferenceFieldUpdater$AtomicReferenceFieldUpdaterImpl from shared objects file]
[Loaded sun.reflect.misc.ReflectUtil from shared objects file]
[Loaded java.io.FilterOutputStream from shared objects file]
[Loaded java.io.PrintStream from shared objects file]
[Loaded java.io.BufferedOutputStream from shared objects file]
[Loaded java.io.Writer from shared objects file]
[Loaded java.io.OutputStreamWriter from shared objects file]
[Loaded sun.nio.cs.StreamEncoder from shared objects file]
[Loaded sun.security.action.GetPropertyAction from shared objects file]
[Loaded java.nio.charset.CharsetEncoder from shared objects file]
[Loaded sun.nio.cs.UTF_8$Encoder from shared objects file]
[Loaded java.io.BufferedWriter from shared objects file]
[Loaded java.lang.Runtime from shared objects file]
[Loaded java.io.File from shared objects file]
[Loaded java.io.FileSystem from shared objects file]
[Loaded java.io.UnixFileSystem from shared objects file]
[Loaded java.io.ExpiringCache from shared objects file]
[Loaded java.util.LinkedHashMap from shared objects file]
[Loaded java.io.ExpiringCache$1 from shared objects file]
[Loaded java.util.LinkedHashMap$Entry from shared objects file]
[Loaded sun.misc.JavaIODeleteOnExitAccess from shared objects file]
[Loaded java.io.File$1 from shared objects file]
[Loaded java.lang.ClassLoader$3 from shared objects file]
[Loaded java.lang.StringCoding$StringEncoder from shared objects file]
[Loaded java.io.ExpiringCache$Entry from shared objects file]
[Loaded java.lang.ClassLoader$NativeLibrary from shared objects file]
[Loaded java.lang.Terminator from shared objects file]
[Loaded sun.misc.SignalHandler from shared objects file]
[Loaded java.lang.Terminator$1 from shared objects file]
[Loaded sun.misc.Signal from shared objects file]
[Loaded sun.misc.NativeSignalHandler from shared objects file]
[Loaded java.io.Console from shared objects file]
[Loaded sun.misc.JavaIOAccess from shared objects file]
[Loaded java.io.Console$1 from shared objects file]
[Loaded java.io.Console$1$1 from shared objects file]
[Loaded java.lang.Shutdown from shared objects file]
[Loaded java.util.ArrayList from shared objects file]
[Loaded java.lang.Shutdown$Lock from shared objects file]
[Loaded java.lang.ApplicationShutdownHooks from shared objects file]
[Loaded java.util.IdentityHashMap from shared objects file]
[Loaded sun.misc.OSEnvironment from shared objects file]
[Loaded sun.misc.JavaLangAccess from shared objects file]
[Loaded java.lang.System$2 from shared objects file]
[Loaded java.lang.NullPointerException from shared objects file]
[Loaded java.lang.ArithmeticException from shared objects file]
[Loaded java.lang.Compiler from shared objects file]
[Loaded java.lang.Compiler$1 from shared objects file]
[Loaded sun.misc.Launcher from shared objects file]
[Loaded java.net.URLStreamHandlerFactory from shared objects file]
[Loaded sun.misc.Launcher$Factory from shared objects file]
[Loaded java.security.SecureClassLoader from shared objects file]
[Loaded java.net.URLClassLoader from shared objects file]
[Loaded sun.misc.Launcher$ExtClassLoader from shared objects file]
[Loaded sun.security.util.Debug from shared objects file]
[Loaded sun.misc.JavaNetAccess from shared objects file]
[Loaded java.net.URLClassLoader$7 from shared objects file]
[Loaded java.util.Enumeration from shared objects file]
[Loaded java.util.StringTokenizer from shared objects file]
[Loaded java.security.PrivilegedExceptionAction from shared objects file]
[Loaded sun.misc.Launcher$ExtClassLoader$1 from shared objects file]
[Loaded sun.misc.MetaIndex from shared objects file]
[Loaded java.io.Reader from shared objects file]
[Loaded java.io.BufferedReader from shared objects file]
[Loaded java.io.InputStreamReader from shared objects file]
[Loaded java.io.FileReader from shared objects file]
[Loaded sun.nio.cs.StreamDecoder from shared objects file]
[Loaded java.lang.reflect.Array from shared objects file]
[Loaded sun.net.[www.ParseUtil](www.ParseUtil) from shared objects file]
[Loaded java.util.BitSet from shared objects file]
[Loaded java.io.ObjectStreamClass from shared objects file]
[Loaded java.net.URL from shared objects file]
[Loaded java.util.Locale from shared objects file]
[Loaded java.util.concurrent.ConcurrentMap from shared objects file]
[Loaded java.util.concurrent.ConcurrentHashMap from shared objects file]
[Loaded java.util.concurrent.locks.Lock from shared objects file]
[Loaded java.util.concurrent.locks.ReentrantLock from shared objects file]
[Loaded java.util.concurrent.ConcurrentHashMap$Segment from shared objects file]
[Loaded java.util.concurrent.locks.AbstractOwnableSynchronizer from shared objects file]
[Loaded java.util.concurrent.locks.AbstractQueuedSynchronizer from shared objects file]
[Loaded java.util.concurrent.locks.ReentrantLock$Sync from shared objects file]
[Loaded java.util.concurrent.locks.ReentrantLock$NonfairSync from shared objects file]
[Loaded java.util.concurrent.locks.AbstractQueuedSynchronizer$Node from shared objects file]
[Loaded java.util.concurrent.ConcurrentHashMap$HashEntry from shared objects file]
[Loaded java.lang.CharacterData from shared objects file]
[Loaded java.lang.CharacterDataLatin1 from shared objects file]
[Loaded java.net.Parts from shared objects file]
[Loaded java.net.URLStreamHandler from shared objects file]
[Loaded sun.net.[www.protocol.file.Handler](www.protocol.file.Handler) from shared objects file]
[Loaded java.util.HashSet from shared objects file]
[Loaded sun.misc.URLClassPath from shared objects file]
[Loaded sun.net.[www.protocol.jar.Handler](www.protocol.jar.Handler) from shared objects file]
[Loaded sun.misc.Launcher$AppClassLoader from shared objects file]
[Loaded sun.misc.Launcher$AppClassLoader$1 from shared objects file]
[Loaded java.lang.SystemClassLoaderAction from shared objects file]
java version "1.6.0_18"
OpenJDK Runtime Environment (IcedTea6 1.8.1) (6b18-1.8.1-0ubuntu1)
OpenJDK Client VM (build 16.0-b13, mixed mode, sharing)
[Loaded java.util.ArrayList$Itr from /usr/lib/jvm/java-6-openjdk/jre/lib/rt.jar]
[Loaded java.util.IdentityHashMap$KeySet from shared objects file]
[Loaded java.util.IdentityHashMap$IdentityHashMapIterator from shared objects file]
[Loaded java.util.IdentityHashMap$KeyIterator from shared objects file]
[Loaded java.io.DeleteOnExitHook from shared objects file]
[Loaded java.util.LinkedHashSet from shared objects file]
[Loaded java.util.HashMap$KeySet from shared objects file]
[Loaded java.util.LinkedHashMap$LinkedHashIterator from shared objects file]
[Loaded java.util.LinkedHashMap$KeyIterator from shared objects file]
[Loaded java.util.Collections from shared objects file]
[Loaded java.util.Collections$EmptySet from shared objects file]
[Loaded java.util.Collections$EmptyList from shared objects file]
[Loaded java.util.Collections$EmptyMap from shared objects file]

---

### Post by jackechanprime on 2010-08-24
oh, and i'm using the most up to date ubuntu version. 10.04 LTS apparently.

so... erm...

now what? i hope it's not just me, but the java -verbose command certainly didn't seem to spit out a directory, at least not one that i readily recognize as "oh, it's that one!"

hope i'm not being an absolute noob, and i do appriciate the help. I really am trying to get this fixed. (note the $2k riding on this program)

---

### Post by spjackson on 2010-08-24
> **jackechanprime said:**
> oh, and i'm using the most up to date ubuntu version. 10.04 LTS apparently.

so... erm...

now what? i hope it's not just me, but the java -verbose command certainly didn't seem to spit out a directory, at least not one that i readily recognize as "oh, it's that one!"

hope i'm not being an absolute noob, and i do appriciate the help. I really am trying to get this fixed. (note the $2k riding on this program)

This path appears 4 times in the output you pasted: /usr/lib/jvm/java-6-openjdk/jre/lib/rt.jar

I would hazard a guess that /usr/lib/jvm/java-6-openjdk/jre/lib/ext might be the path you want, but hold fire a moment. You did not mention in your original post that you need Firefox to have access to this, but you did mention it in a follow up. In that case, let's check something else.

```
ls -l /usr/lib/mozilla/plugins/
```On my system this lists (among others) libjavaplugin.so -> /etc/alternatives/mozilla-javaplugin.so

So

```
ls -l /etc/alternatives/mozilla-javaplugin.so
```and, again on my system, this shows a symbolic link to /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/IcedTeaPlugin.so

and from that, we deduce that /usr/lib/jvm/java-6-openjdk/jre/lib/ext is a good candidate.

But this depends on what these show on your system - and whether you have over-ridden the default plugin in ~/.mozilla/...

---

### Post by jackechanprime on 2010-08-24
Heres the terminal for those two codes:

jackechan@jackechan-laptop:~$ ls -l /usr/lib/mozilla/plugins/
total 392
lrwxrwxrwx 1 root root     37 2010-08-15 18:37 flashplugin-alternative.so -> /etc/alternatives/mozilla-flashplugin
lrwxrwxrwx 1 root root     39 2010-08-16 15:20 libjavaplugin.so -> /etc/alternatives/mozilla-javaplugin.so
-rw-r--r-- 1 root root   5400 2010-06-25 04:01 librhythmbox-itms-detection-plugin.so
-rw-r--r-- 1 root root 100328 2010-05-19 07:38 libtotem-cone-plugin.so
-rw-r--r-- 1 root root 108864 2010-05-19 07:38 libtotem-gmp-plugin.so
-rw-r--r-- 1 root root  75740 2010-05-19 07:38 libtotem-mully-plugin.so
-rw-r--r-- 1 root root  84100 2010-05-19 07:38 libtotem-narrowspace-plugin.so
jackechan@jackechan-laptop:~$ ls -l /etc/alternatives/mozilla-javaplugin.so
lrwxrwxrwx 1 root root 57 2010-08-16 15:20 /etc/alternatives/mozilla-javaplugin.so -> /usr/lib/jvm/java-6-openjdk/jre/lib/i386/IcedTeaPlugin.so

Sorry about that omission, I'm only dimly aware of the other applications that Java programs have outside of firefox, and forgot that it'd be pertinent to mention that i was using it in my browser. Apologies again.

sooo...

should try "firing" on /usr/lib/jvm/java-6-openjdk/jre/lib/ext then? Seems like I'm getting the same general output as you (although I'd prefer it if more knowing eyes then mine confirmed that)... so i guess that'd be the right directory to try it on?

---

### Post by jackechanprime on 2010-08-24
so... yes or no? should i give it a go?

...well... i guess I'll try it and see if it works then?

the silence from you guys is mildly unnerving...

---

### Post by jackechanprime on 2010-08-24
ok, i put it in the directory... lets see if it works...

---

### Post by tylerdurdin on 2010-08-24
[http://nfolamp.wordpress.com/2010/05/19/howto-install-sun-java-on-ubuntu-10-04-lucid/](http://nfolamp.wordpress.com/2010/05/19/howto-install-sun-java-on-ubuntu-10-04-lucid/)

I had crazy java problems too and thought i did what this link says a thousand times but i followed this link and everything worked perfect including frostwire which everytime i ever installed failed due to something java related. you may wannna give it a shot if you cant find anything else.

---

### Post by jackechanprime on 2010-08-24
IT WORKED!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!111!!!!!!!!!1!!!one!!!!!!!11!

thanks a bunch guys!!!
program is up and running =]

again, thanks a ton,
~Q

---

### Post by spjackson on 2010-08-25
> **jackechanprime said:**
> Heres the terminal for those two codes:

jackechan@jackechan-laptop:~$ ls -l /usr/lib/mozilla/plugins/
total 392
lrwxrwxrwx 1 root root     37 2010-08-15 18:37 flashplugin-alternative.so -> /etc/alternatives/mozilla-flashplugin
lrwxrwxrwx 1 root root     39 2010-08-16 15:20 libjavaplugin.so -> /etc/alternatives/mozilla-javaplugin.so
-rw-r--r-- 1 root root   5400 2010-06-25 04:01 librhythmbox-itms-detection-plugin.so
-rw-r--r-- 1 root root 100328 2010-05-19 07:38 libtotem-cone-plugin.so
-rw-r--r-- 1 root root 108864 2010-05-19 07:38 libtotem-gmp-plugin.so
-rw-r--r-- 1 root root  75740 2010-05-19 07:38 libtotem-mully-plugin.so
-rw-r--r-- 1 root root  84100 2010-05-19 07:38 libtotem-narrowspace-plugin.so
jackechan@jackechan-laptop:~$ ls -l /etc/alternatives/mozilla-javaplugin.so
lrwxrwxrwx 1 root root 57 2010-08-16 15:20 /etc/alternatives/mozilla-javaplugin.so -> /usr/lib/jvm/java-6-openjdk/jre/lib/i386/IcedTeaPlugin.so

Sorry about that omission, I'm only dimly aware of the other applications that Java programs have outside of firefox, and forgot that it'd be pertinent to mention that i was using it in my browser. Apologies again.

sooo...

should try "firing" on /usr/lib/jvm/java-6-openjdk/jre/lib/ext then? Seems like I'm getting the same general output as you (although I'd prefer it if more knowing eyes then mine confirmed that)... so i guess that'd be the right directory to try it on?

Yes. Based on the instructions in your original post and the output you've shown, that would be reasonable.

---

