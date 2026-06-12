---
title: "Memory usage without swap under OpenVZ"
date: 2012-06-05
forum: General Help
---

### Post by jarlanddonnell on 2012-06-05
I've been searching extensively for several days, both here and elsewhere. My question relates to the usage of Ubuntu under OpenVZ virtualization. At this moment, most providers have not enabled the vswap feature in OpenVZ. Because of this I am able to run into an issue that tests my understanding of how Linux operates and I simply need some guidance. This issue is not limited to Ubuntu, I simply prefer Ubuntu. I apologize for the wall of text here, I just want to be thorough.

The problem:
With no swap available, memory usage on Ubuntu (specifically referring to running a GUI, not your average server applications) goes through the roof. Let's say that I install ubuntu-desktop on an OpenVZ system and start it up in VNC, with no optimizations. I'm running roughly 950MB-1.5GB of memory usage. I am not misunderstanding usage here. This is not cached, this is in use.

The monkey wrench:
I create a fake 512MB swap. This is not real. This swap is not used, cannot be used, and is nothing more than smoke and mirrors. Same scenario, my memory usage drops to 250-300MB.

Summary of my understanding:
I understand that any application that attempts to utilize the fake swap will, in this case, crash horribly. What confuses me is that absolutely no application that I use on this system (these are desktop apps, this is a remote VNC machine) has a single issue. In fact, the applications launch faster. I do not notice a significant increase in I/O, almost no fluctuation in RAM usage.

The actual question:
If these applications need swap to run efficiently, load fully into RAM when swap is not an option, and function absolutely flawlessly at a fraction of the memory usage by the mere appearance of the availability of swap, how does this make sense?

I appreciate anyone willing to take a moment to explain this to me if they understand how this is taking place and what the benefits or consequences, or alternative remedies may be.

---

### Post by Siana on 2012-07-18
How do you create a fake swap? Is this the well-known shell script which replaces /proc/meminfo with a fake? Cause i frankly don't think you can fool the linux kernel easily like that! I will present a theory, which however will pretty much collapse if that's what you did.

Some commercial applications do checking apropos free ram and available swap, and they may need such a trick, but that's obviously not the reason you need swap in your case.

Difference between having a swap and not having a swap can be explained by  a bug, or design decision, in your distro or kernel. I'm not SUPER familiar with the topic, not being a kernel developer, but i'll lay out how i imagine things. There are a number of values which tune the behaviour of linux kernel apropos management of memory pages. You can see one of these as a tunable value, in /proc/sys/vm/swappiness. It should default to so 50-60-ish.

On a machine with swap, you can try setting swappiness to 0 and see whether it will behave like a machine without swap.

On a machine without swap, you can try looking what the value looks like, and seeing whether bumping it helps.

The one theory that comes to my mind, is that on machine without swap, vm. swappiness value is either set to 0, or treated as if it was 0. Then also you have to know, that it doesn't only control swap disk consumption. There is such a thing as swapping without the swap file, which is used in combination, and even in preference to swap, and i believe vm.swappiness value controls both writing to swap-file, and paging out of the pages not backed by swap disk.

You have to know, that many dynamic runtimes, like Python, Java and Mono, and many major UI libraries and desktop frameworks, don't actually load files by reading them piece by piece. This is inefficient. Instead, they "map" files into memory. This same mechanism is used for loading executables and shared libraries. Memory is merely reserved, and the kernel pretends as if the file is already completely in memory. When a program accesses this region of memory, either the data is genuinely already there, or the kernel interrupts the program (by intercepting an access fault), fetches the data, puts it where the program expects it, and resumes the program making the memory access succeed. The memory that has been reserved is also not physical memory, it's merely memory from the program's point of view, i.e. a region of address space, which, in the case when the data hasn't been loaded yet, usually does not correspond to any RAM portion. Also keep in mind that every program runs in its own address space, in its own view of memory where it is the king, there is some space for the kernel, and the rest doesn't exist. Depending on how much of this you knew beforehand, your mind might be boggled, or you might already be used to the sheer complexity of this.

Besides satisfying the program's immediate need for data, the kernel may use predictions to satisfy program's need for data in advance, which will reduce switching of execution context between program and kernel and improves efficiency. If the data is already fetched and cached, why not give it to program immediately?

Due to this, the software faces the situation, that data has been loaded, and consumes RAM, which has never been needed, or is not needed any longer. For a long time i have imagined that the kernel would simply once in a while invalidate pages in a program, while retaining them in cache, and count page faults which occur. This turns out to be exactly true for systems with simple memory management hardware, such as ARM and SuperH, which i used to work with and seeing the CPU manual, didn't really see another way for this to be done. If the page remains in the cache long enough, it can be swapped out. But as desktop computers have a LOT of pages these days, i wasn't sure, so i checked, recent Intel-compatible CPUs actually have flag "A" in page tables, which can be cleared at will and will be set when some someone accesses a page, allowing to estimate the usage of a particular page in a lightweight manner. The most trivial implementation of that will keep the pages accounted as used and not cached in this case, as opposed to the implementation which is needed on simple memory management units. However, less used read only pages can be purged on demand just as easily as if they were mere cache.

In the end effect, you can see mapped files as being initially swapped out to the disk where they come from, being swapped in as they're used, and swapped out to the disk where they came from eventually. In the case of writable files, it means file pages will wander into the write cache. In the case of read-only open files, it means nothing has to be done AT ALL.

Mapping files into memory makes accounting of actual memory consumption SUPER complicated! Especially considering multiple programs, if each maps the same set of files, you will see memory consumption of each skyrocket, but the actual memory consumption will be mere bytes per program per file!

At the end of the day, the disadvantage of having a high memory consumption reading on systems without swap may or may not be there, and is most likely the artifact of accounting, depending on so many details in the kernel implementation, depending on so many things, so it probably makes sense just to benchmark. I have a feeling, that in case of runtimes which use any delayed kind of garbage collection, such as Java, Mono and Ruby, the difference in accounting may actually make a difference in behavior, forcing them to collect more often, and drive them to conserve RAM but waste CPU time. If you have nowhere to swap their excess memory baggage out to, it might not even be a bad choice.

---

### Post by Siana on 2012-07-19
Even better and shorter answer: OpenVZ memory accounting isn't the same as Linux kernel's memory accounting, it blatantly lies, or at least used to, tending to report virtual size instead of actual, making all your mapped files contribute to the consumption. With the introduction of vswap, it gained new kind of accounting where it's very very similar to behaviour of standard Linux kernel. However the old accounting may still be available, and chances are, you're triggering a change in accounting somehow?

---

