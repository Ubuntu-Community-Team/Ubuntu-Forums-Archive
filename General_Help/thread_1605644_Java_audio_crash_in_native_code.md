---
title: "Java audio crash in native code"
date: 2010-10-25
forum: General Help
---

### Post by wrldwzrd89 on 2010-10-25
java: /build/buildd/openjdk-6-6b20-1.9/build/../pulseaudio/src/native/org_classpath_icedtea_pulseaudio_Stream.c:680: Java_org_classpath_icedtea_pulseaudio_Stream_native_1pa_1stream_1cork: Assertion `stream' failed.

I keep getting this error about 1-10% of the time when a Java application tries to play audio. When this happens, the whole JVM quits, which means the crash is in native code. I find it difficult to test my Java games, for obvious reasons, since I am a Java developer primarily. I use Eclipse 3.6 SR1 to develop my Java apps, and I'm a recent convert to Ubuntu from Mac OS X.

EDIT: Whoops, forgot to mention that I'm running Ubuntu 10.10 "Maverick Meerkat" x86_64 version.

---

### Post by lykeion on 2010-10-26
It's hard to tell what's failing without any relevant source code.
Do you use javazoom/libbasicplayer? If so these links may be of some help:
[http://stackoverflow.com/questions/1914216/master-gain-not-supported-in-openjdk](http://stackoverflow.com/questions/1914216/master-gain-not-supported-in-openjdk)
[https://bugs.launchpad.net/ubuntu/+source/libbasicplayer-java/+bug/491784](https://bugs.launchpad.net/ubuntu/+source/libbasicplayer-java/+bug/491784)

Also you could try to switch to sun-java6-jdk and see if it helps.

But post the relevant audio playing code, it'd easier to test and find out what's causing the error.

---

### Post by wrldwzrd89 on 2010-10-26
> **lykeion said:**
> It's hard to tell what's failing without any relevant source code.
Do you use javazoom/libbasicplayer? If so these links may be of some help:
[http://stackoverflow.com/questions/1914216/master-gain-not-supported-in-openjdk](http://stackoverflow.com/questions/1914216/master-gain-not-supported-in-openjdk)
[https://bugs.launchpad.net/ubuntu/+source/libbasicplayer-java/+bug/491784](https://bugs.launchpad.net/ubuntu/+source/libbasicplayer-java/+bug/491784)

Also you could try to switch to sun-java6-jdk and see if it helps.

But post the relevant audio playing code, it'd easier to test and find out what's causing the error.
I don't use either of those two libraries.
I'm not quite sure how to post the source code, since the actual audio playback code and the code that uses said playback code are in completely different packages. What I can do is post a link to the (zipped) source for the project in question: [http://lasertank.worldwizard.net/prelim/LaserTankSource.zip](http://lasertank.worldwizard.net/prelim/LaserTankSource.zip) (direct link) or [http://lasertank.worldwizard.net/](http://lasertank.worldwizard.net/) (web site where code lives).

---

### Post by lykeion on 2010-10-26
Ok, I tested your source and it's a nice game :)
However there was no sound at all in the game when I played it (even though sound was enabled).

Browsed through your Sound and SoundManager classes and they seemed ok, so I don't know why there was no sound.

Could you try this simple audio player and see if you can experience the same crash:

[PHP]import javax.sound.sampled.*;
import java.io.File;
import java.io.IOException;

public class SoundPlayer extends Thread {

    private final int EXTERNAL_BUFFER_SIZE = 524288; // 128Kb
    String filename = "res/die.wav";

    public void run() {
        
        File soundFile = new File(filename);

        AudioInputStream audioInputStream = null;
        AudioFormat format = null;
        SourceDataLine line = null;
        
        try {
            audioInputStream = AudioSystem.getAudioInputStream(soundFile);
            format = audioInputStream.getFormat();
        } catch (UnsupportedAudioFileException e) {
            e.printStackTrace();
        } catch (IOException e) {
            e.printStackTrace();
        }

        DataLine.Info info = new DataLine.Info(SourceDataLine.class, format);

        try {
            line = (SourceDataLine) AudioSystem.getLine(info);
            line.open(format);
        } catch (LineUnavailableException e) {
            e.printStackTrace();
        }

        line.start();
        
        int nBytesRead = 0;
        byte[] abData = new byte[EXTERNAL_BUFFER_SIZE];

        try {
            while (nBytesRead != -1) {
                nBytesRead = audioInputStream.read(abData, 0, abData.length);
                if (nBytesRead >= 0)
                { line.write(abData, 0, nBytesRead); }
            }
        } catch (IOException e) {
            e.printStackTrace();
            return;
        } finally {
            line.drain();
            line.close();
        }
    }
}
[/PHP]

---

### Post by wrldwzrd89 on 2010-10-26
I tried the posted code, after setting everything up (creating an Eclipse workspace, creating a project, creating the res folder, copying the die.wav sound to it, etc.), and... it does not crash. I've run it about 10 times, and it has worked flawlessly every time.

---

### Post by lykeion on 2010-10-26
Ok, that's good then. Maybe you could try to use SourceDataLine instead of Clip in Sound.getData()

Also I'd suggest you output stacktrace/debug info on every catch clause and if-check you have in your sound and sound manager classes, so that you can pinpoint where these crashes occur.

Another suggestion is to switch to Sun Java JDK. It's more stable than bleeding-edge OpenJDK.

---

### Post by wrldwzrd89 on 2010-10-26
Got rid of that error with several changes to Sound.java and SoundManager.java, but I've introduced another:

[php]
Exception in thread "PulseAudio Eventloop Thread" java.lang.IllegalStateException: drain failed
	at org.classpath.icedtea.pulseaudio.EventLoop.native_iterate(Native Method)
	at org.classpath.icedtea.pulseaudio.EventLoop.run(EventLoop.java:141)
	at java.lang.Thread.run(Thread.java:636)
[/php]

Sound.java:
[php]
/*  LaserTank: An Arena-Solving Game
Copyright (C) 2008-2010 Eric Ahnell

Any questions should be directed to the author via email at: lasertank@worldwizard.net
 */
package net.worldwizard.audio;

import java.io.IOException;
import java.net.URL;

import javax.sound.sampled.AudioFileFormat;
import javax.sound.sampled.AudioFormat;
import javax.sound.sampled.AudioInputStream;
import javax.sound.sampled.AudioSystem;
import javax.sound.sampled.DataLine;
import javax.sound.sampled.LineUnavailableException;
import javax.sound.sampled.SourceDataLine;
import javax.sound.sampled.UnsupportedAudioFileException;

public class Sound {

	// Fields
	private URL url;
	private AudioInputStream stream;
	private AudioFileFormat fileFormat;
	private AudioFormat format;
	private SourceDataLine line;
	private DataLine.Info info;
	private static final int EXTERNAL_BUFFER_SIZE = 524288; // 128Kb

	public Sound(final URL loc) {
		this.url = loc;
	}

	private void getData() {
		try {
			this.stream = AudioSystem.getAudioInputStream(this.url);
			this.fileFormat = AudioSystem.getAudioFileFormat(this.url);
			this.format = this.fileFormat.getFormat();
			this.info = new DataLine.Info(SourceDataLine.class, this.format);
			if (AudioSystem.isLineSupported(this.info)) {
				try {
					this.line = (SourceDataLine) AudioSystem.getLine(this.info);
					this.line.open(this.format, EXTERNAL_BUFFER_SIZE);
				} catch (final LineUnavailableException e) {
					// Do nothing
				}
			}
		} catch (final UnsupportedAudioFileException e) {
			// Do nothing
		} catch (final IOException e) {
			// Do nothing
		}
	}

	public void play() {
		this.getData();
		if (this.line != null) {
			this.line.start();
			int nBytesRead = 0;
			byte[] abData = new byte[Sound.EXTERNAL_BUFFER_SIZE];
			try {
				while (nBytesRead != -1) {
					nBytesRead = this.stream.read(abData, 0, abData.length);
					if (nBytesRead >= 0) {
						this.line.write(abData, 0, nBytesRead);
					}
				}
				this.line.drain();
				this.line.close();
			} catch (IOException e) {
				return;
			}
		}
	}
}
[/php]

SoundManager.java:
[php]
/*  LaserTank: An Arena-Solving Game
Copyright (C) 2008-2010 Eric Ahnell

Any questions should be directed to the author via email at: lasertank@worldwizard.net
 */
package net.worldwizard.lasertank.resourcemanagers;

import java.net.URL;
import java.nio.BufferUnderflowException;

import net.worldwizard.audio.Sound;
import net.worldwizard.lasertank.LaserTank;
import net.worldwizard.lasertank.prefs.PreferencesManager;

public class SoundManager {

	private static final String DEFAULT_LOAD_PATH = "/net/worldwizard/lasertank/resources/sounds/";
	private static String LOAD_PATH = SoundManager.DEFAULT_LOAD_PATH;
	private static Class<?> LOAD_CLASS = SoundManager.class;

	private static Sound getSound(final String filename) {
		// Get it from the cache
		return SoundCache.getCachedSound(filename);
	}

	static Sound getUncachedSound(final String filename) {
		try {
			final URL url = SoundManager.LOAD_CLASS
					.getResource(SoundManager.LOAD_PATH
							+ filename.toLowerCase() + ".wav");
			final Sound snd = new Sound(url);
			return snd;
		} catch (final NullPointerException np) {
			return null;
		}
	}

	public static void playSound(final int soundID) {
		if (PreferencesManager.getSoundsEnabled()) {
			new Thread() {
				@Override
				public void run() {
					try {
						final String soundName = SoundConstants.SOUND_NAMES[soundID];
						final Sound snd = SoundManager.getSound(soundName);
						if (snd != null) {
							// Play the sound
							try {
								snd.play();
							} catch (BufferUnderflowException bue) {
								// Ignore
							} catch (NullPointerException np) {
								// Ignore
							} catch (Throwable t) {
								LaserTank.getDebug().debug(t);
							}
						}
					} catch (ArrayIndexOutOfBoundsException aioob) {
						// Do nothing
					}
				}
			}.start();
		}
	}

	public static void useCustomLoadPath(final String customLoadPath,
			Object plugin) {
		SoundManager.LOAD_PATH = customLoadPath;
		SoundManager.LOAD_CLASS = plugin.getClass();
		SoundCache.flushCache();
	}

	public static void useDefaultLoadPath() {
		SoundManager.LOAD_PATH = SoundManager.DEFAULT_LOAD_PATH;
		SoundManager.LOAD_CLASS = SoundManager.class;
		SoundCache.flushCache();
	}
}
[/php]

---

### Post by wrldwzrd89 on 2010-10-26
After fooling around with the sound code a bit more (I removed the sound cache, so Sound objects don't get reused), the second error has gone away. Sound now plays properly on my development machine, in Java.

---

### Post by lykeion on 2010-10-26
That's brilliant, and good luck with the game. It's looking really good so far. I especially like the editor.

In Sound.play() I'd still put the close() method call (and maybe also drain() method) in a finally clause to guarantee the execution of these.

---

### Post by wrldwzrd89 on 2010-10-26
Made the change to Sound.java, as suggested. Playback still works.

Thank you for your help.

---

