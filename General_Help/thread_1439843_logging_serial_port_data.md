---
title: "logging serial port data"
date: 2010-03-26
forum: General Help
---

### Post by gfuggs on 2010-03-26
I am not looking to write data out to the serial port.
I am not looking to read data in from the serial port.

I have a program running that is communicating through the serial port, and I want to monitor what is going out and coming in.

I need to be able to monitor it in real time.  In Windows, there is a utility called portmon that logs all serial port data to a file.  I think I need something similar.

I tried a utility called ttylog, and I redirected its output to a file, but the file stays at 0 bytes until everything is done with.  Is there a way to redirect to a file, but have the data written to disk as it comes in rather than at the end?

I am attempting to extract certain data that is going through the serial port, and plot it in real time as it comes through.  Any other suggestions for doing this?

---

### Post by dcstar on 2010-03-26
> **gfuggs said:**
> I am not looking to write data out to the serial port.
I am not looking to read data in from the serial port.

I have a program running that is communicating through the serial port, and I want to monitor what is going out and coming in.

I need to be able to monitor it in real time.  In Windows, there is a utility called portmon that logs all serial port data to a file.  I think I need something similar.

I tried a utility called ttylog, and I redirected its output to a file, but the file stays at 0 bytes until everything is done with.  Is there a way to redirect to a file, but have the data written to disk as it comes in rather than at the end?

I am attempting to extract certain data that is going through the serial port, and plot it in real time as it comes through.  Any other suggestions for doing this?

```
man tee
```

---

