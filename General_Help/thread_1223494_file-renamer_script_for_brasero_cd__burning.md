---
title: "file-renamer script for brasero cd  burning"
date: 2009-07-26
forum: General Help
---

### Post by instantkarma on 2009-07-26
hi,

I have this glitch with brasero where when I burn mp3 cds brasero burns the files ordered by name and not by album/artist when the file is named in the "01-songname-artist" format. In essence actual song order on the cd will be "01-songname-artist", "01-songname-differentartist", "01-songname-thirdartist"..."02-songname-artist", "02-songname-differentartist", "02-songname-thirdartist" and so on and albums that you would want to play consecutively don't. The solution to this issue is to simply rename the prefix of the file so that brasero will burn the songs according to artist/album as it burns according to alphabetical order. i.e. "prefix1-01-songname-artist", "prefix1-02-songname-artist", "prefix1-03-songname-artist"..."prefix2-01-songname-artist", "prefix2-02-songname-artist", "prefix2-03-songname-artist" and so on.

I wrote a script in Java that automates this for you:

```

import java.io.Console;
import java.io.File;
import java.io.IOException;

public class FileRename {

	/**
	 * @param args
	 * @throws IOException
	 */
	public static void main(String[] args) {
		if (args.length < 1) {
			System.err.println("Error: No directory was chosen.");
			System.exit(0);
		}
		File dir = new File(args[0]);
		File[] listFiles = dir.listFiles();
		Console c = System.console();
		int length = 3;
		if (args.length == 2) {
			try {
				length = Integer.parseInt(args[1]);
			} catch (Exception e) {
				System.out.println("Invalid length value given. use default? y/n");
				String ans = c.readLine();
				c.flush();
				if (!ans.equals("y")){
					System.exit(0);
				}
			}
		}
		while (listFiles[0].isDirectory()) {
			dir = listFiles[0];
			listFiles = dir.listFiles();
		}
		for (File f : listFiles) {
			if (f.getName().endsWith("3")) {
				f.renameTo(new File(f.getParent() + "/"
						+ dir.getName().substring(0, length) + "_"
						+ f.getName()));
			}
		}
		
	}

}

``` 

Simply copy paste the code into an empty text file and name the file "FileRename.java" (has to be that name). 

Then run:
```
javac FileRename.java
```
(only needed the initial time, the rest of the time skip to the next step)

then, say, your much needed to be renamed mp3s are in your "/home/<username>/Music/<artist>" directory then all you do is:

```
java FileRename "/home/<username>/Music/<artist>"
```

and your mp3 files are prefixed with the first 3 letters of the <artist>'s folder's name. 

Any comments or ideas are very much welcome.

---

