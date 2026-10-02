#my-website
This is my personal website — a space to showcase who I am, what I build, and the ideas I’m exploring. It brings together my projects, experiments, interests, and a little bit of my personality in one place.


The Logic Behind Each Page
1. index.html (Intro / About Me)

This is the front door. It has no JavaScript. It is all layout and CSS.
As a beginner this page helped me learn a lot. I had a lot of ideas that I couldn't implement and many in which I had to go to youtube and back again and again to learn. As it is obvious the background has a pixelated sky image with another dark gradient on top to make sure the other elements of the page standout. I learned the hard way but using fixed it kept the picture still though the picture did zoom in by a lot and i tried to make it less pixelated I kept messing it up. The final product turned out alright I would say.

GIF box: After a lot of experimentation with the sixes i came to the conclusion of this fixed-height box with a glowing purple border (box-shadow). The image inside uses object-fit: cover so it fills the box without stretching. I had to search this on youtube and other html sites. This really makes you realise how many minute details go into every design.

Scrolling marquee: the "WELCOME TO MY SYSTEM" text repeats several times inside a wider-than-screen span. A CSS @keyframes scroll animation moves it left with translateX, and it loops forever. Repeating the text means there's always text on screen while it moves. This was the hardest thing on this page, as I kept getting the loop timing wrong and it didn't fit right. After a lot of trial and error I ended up fixing it.


Info boxes: "About Me" and "Hobbies" are tables inside neon-bordered boxes. I used a table because the content is naturally label → value pairs, and td:first-child styles all the labels in one rule.
Enter button: a normal link (<a>) styled like a button. On hover it flips from outlined to filled with a glow, using a transition so it fades smoothly. I saw those cool references on pinterest and the thing I created doesn't come close yet, I know but it's alright because I think it looks good in my opinion.

2. PC.html (The Computer, the Heart of the Site, The Hardest Part)

This is the most interactive page. The idea: a monitor that starts "off" and boots up. I wanted to make it more futuristic but I couldn't make the gui and so I decided to go for something simpler that I could do.

The monitor: a rounded dark frame (.monitor) containing a .screen. Everything on the screen lives inside .screen-content, which is hidden (display: none) until the PC is turned on.
Turn on (turnOn()): adds an on class to the screen (which changes its background to purple with an inner glow), hides the TURN ON button, shows the desktop, plays the power-on sound and background music, then starts the typing animation and the clock. .catch(()=>{}) is there because browsers sometimes block autoplay audio, and this stops that from throwing an error.
Shut down (shutDown()): does the reverse. It removes the classes, closes popups, pauses the music and resets it to the start (currentTime = 0), clears the welcome text, and stops the clock with clearInterval.
Typing effect (typeWelcome()): a setInterval adds one letter of "Welcome to my system" every 100ms. When the index reaches the end of the text, it clears itself.
Live clock (updateClock()): new Date() gives the current time. It's formatted with toLocaleTimeString / toLocaleDateString, then written into the top-right display, the taskbar button and the calendar popup. setInterval re-runs it every second.


Folders: four links (Music, Gaming, Notes, Media) laid out in a column. On hover, the icon plays a small shake animation so it feels clickable and interactive! Others can use this by changing the folders or infact adding more folders/apps and personalise their own personal site.  


Popups: the calendar and chat are hidden boxes positioned just above the taskbar. toggleCalendar() and toggleChat() flip a show class, and each one closes the other so only one is open at a time.


Chat bot: the first time chat opens, a forEach loop adds three messages, each delayed by index * 900 ms so they appear one after another like someone typing. A chatStarted flag stops it from repeating. The last message 'saanvi' hyperlinks to socials.html. This chat bot was added to show a bit of personality. Though all my interests have been layed out despite that I still wanted my fun and personality to pop through, which i included in tiny ways through this chat bot that appears again in the music file.


3. socials.html (Find Me Elsewhere)

A fake "search engine" for finding my socials.

The input is already there, so you can't type in it. Clicking it opens a dropdown of all the platforms. Originally I wanted people to type it in and then the search to work but I didn't know how that would work out.
selectItem(name, url) puts the platform name in the box, saves the link in a variable (selectedUrl), and closes the dropdown.
goToSelected() opens the saved link in a new tab, but only if something has been selected.
A click listener on the whole document closes the dropdown when you click anywhere outside it (e.target.closest('.search-wrap') checks whether the click was inside the search area).

4. notes.html (A Parting Note)

This page was made so all the small details that people might miss is mentioned. Furthermore a note from me to make the journey of the personal site feel more personal. It is mostly CSS atmosphere, with no JavaScript.


5. music.html (Music Bot)

A small game that unlocks the music.

Floating letter tiles: JavaScript creates five tiles (M, U, S, I, C) and gives each letter a random position. The letter tile can only be clicked in order and after it is done, you can access the music folder.
The very same bot which was in the pc.html: a purple "slime" blob whose shape wobbles through a slime animation (changing border-radius and scale).
Mood system: all four moods are stored in one object, moodData, each with an audio file, a CSS class and a message. playMood() looks up the chosen mood, plays the song, applies that mood's colour class to the blob (the colour shifts using filter: hue-rotate, with a smooth transition), and shows the bot's message. Keeping the data in one object means adding a mood is just adding an entry.


Flow control: clicking the blob stops the song and asks if you want another. YES returns to the mood choices and NO ends the session and sends you back to the PC in a second.

6. media.html (Worlds I've Watched)

A database-style page for shows I've watched. I got lazy so I decided to make it the same for all shows and ended up adding only a few to showcase how it would actually look.

CSS variables (:root) store the colour palette and fonts once, so the whole page can be restyled from one place.
Show cards: each show is an <article> using CSS Grid (44% / 56%): a billboard image on the left and info on the right. On screens under 850px it collapses to one column.
Details: hover zooms the image, the card has a cut corner made with clip-path, and the neon frame is another element that makes the vibe very cyberpunkish.
Animated rating bars (the main JavaScript): every bar starts at width: 0% and stores its score in a data-score attribute. An IntersectionObserver watches the bars and, when one scrolls 45% into view, sets its width to its score. The CSS transition makes it slide in. After that it calls unobserve, so each bar only animates once.
Billboard hover lighting: a small script brightens the image on mouseenter and resets it on mouseleave.


7. gaming.html (Gaming Archive)

A "database entry" layout for each game.

Each game is a <section class="game"> with the same building blocks: a title, a terminal box (the story), a player data box (quick facts), identity cards (username, UID and so on), and memory cards.
Because every game reuses the same classes, adding another game means copying one section and changing the text.
CSS Grid arranges everything (1.5fr 0.7fr for story and data, repeat(4, 1fr) for the identity cards, repeat(3, 1fr) for memories). Media queries stack these on smaller screens.
The glitchy title effect is two offset text-shadows in purple and pink. The big faint numbers behind each entry are positioned absolutely and ignore the mouse.
The page has no JavaScript. It is entirely structure and styling.
Where I Took Help From AI

I wrote the content, structure and logic of the site myself. I used AI for the parts a person can't realistically eyeball, mostly the precise numbers involved in the visual design:

Exact measurements such as sizes, spacing, padding, margins and the grid column splits (for example 44% / 56%)
Fine-tuning values like box-shadow glow strengths, gradient colour stops, opacity levels, blur amounts and animation timings
Responsive breakpoints and clamp() values so the layout still looks right on phones
Debugging and cleaning up small CSS and JavaScript errors

Credits and Notes
Please note the design and the idea are original for this site. I have only taken inspiration from Pinterest and the anime Cyberpunk: Edgerunners to give the site that aesthetic.
Another note: the pictures and audio are not mine. They come from Google and YouTube.


Built With

HTML5 · CSS3 (Grid, Flexbox, animations, gradients) · Vanilla JavaScript · Google Fonts (JetBrains Mono, Rajdhani, Space Mono, DM Mono, Orbitron)

My first complete site. Feel free to connect with me. I'd love to learn from you or make something together!