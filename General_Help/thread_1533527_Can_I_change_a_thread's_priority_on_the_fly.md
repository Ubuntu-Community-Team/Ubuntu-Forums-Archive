---
title: "Can I change a thread's priority on the fly?"
date: 2010-07-18
forum: General Help
---

### Post by Sholto on 2010-07-18
I have an array of threads which must be activated in a certain order, so each can append data to a buffer in the correct sequence.
I started by letting each thread release itself (with pthread_mutex_unlock()), which would activate the next thread, and that thread would in turn check if it was next in line to append its data. If it wasn't, it would unlock the mutex and let another thread have a go.
Trouble is, this is hit or miss. Mostly threads were activated, realised they were not the next in turn, then would de-activate themselves. Eventually the correct thread would be activated and would do its stuff to the buffer.
I tried improving the hit rate by setting the next thread in line to high priority. Hopefully it would then be the next thread to be activated.  This seemed to work using pthreads in Windows - the threads were usually activated in the correct order.
However under Linux this doesn't work.
I set the thread attribute policy to SCHED_OTHER, but setting the priority to high had no effect. I have a feeling that SCHED_OTHER allows only one priority - is this correct?
I then tried different policies, like SCHED_FIFO and SCHED_RR.  However I could then not set the priority - the call to pthread_setschedparam() failed with an 'Invalid argument' message.
Does anyone know how I can dynamically upgrade the priority of a specific thread?

---

