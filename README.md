# Ex05 Image Carousel
## Date:

## AIM
To create a Image Carousel using React 

## ALGORITHM
### STEP 1 Initial Setup:
Input: A list of images to display in the carousel.

Output: A component displaying the images with navigation controls (e.g., next/previous buttons).

### Step 2 State Management:
Use a state variable (currentIndex) to track the index of the current image displayed.

The carousel starts with the first image, so initialize currentIndex to 0.

### Step 3 Navigation Controls:
Next Image: When the "Next" button is clicked, increment currentIndex.

If currentIndex is at the end of the image list (last image), loop back to the first image using modulo:
currentIndex = (currentIndex + 1) % images.length;

Previous Image: When the "Previous" button is clicked, decrement currentIndex.

If currentIndex is at the beginning (first image), loop back to the last image:
currentIndex = (currentIndex - 1 + images.length) % images.length;

### Step 4 Displaying the Image:
The currentIndex determines which image is displayed.

Using the currentIndex, display the corresponding image from the images list.

### Step 5 Auto-Rotation:
Set an interval to automatically change the image after a set amount of time (e.g., 3 seconds).

Use setInterval to call the nextImage() function at regular intervals.

Clean up the interval when the component unmounts using clearInterval to prevent memory leaks.

## PROGRAM
```
INDEX.html
html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Image Carousel</title>
    <link rel="stylesheet" href="style.css">
</head>

<body>

    <div class="carousel">
        <h1>Image Carousel</h1>

        <div class="image-container">
            <img id="carouselImage" src="image1.svg" alt="Mountain landscape">
        </div>

        <div class="buttons">
            <button type="button" onclick="previousImage()">Previous</button>
            <button type="button" onclick="nextImage()">Next</button>
        </div>
    </div>

    <script src="script.js"></script>

</body>
</html>
```

css
```
@import url('https://fonts.googleapis.com/css2?family=DM+Sans:wght@400;500;700&family=Space+Grotesk:wght@500;600;700&display=swap');

:root {
    color-scheme: dark;
    --ink: #f4f1ea;
    --accent: #f3b562;
    --panel: rgba(24, 29, 33, 0.82);
    --line: rgba(244, 241, 234, 0.14);
}

* {
    box-sizing: border-box;
}

body {
    min-height: 100vh;
    margin: 0;
    display: grid;
    place-items: center;
    padding: 32px 18px;
    color: var(--ink);

    background:
        radial-gradient(
            circle at 16% 18%,
            rgba(189, 105, 61, 0.32),
            transparent 30%
        ),
        radial-gradient(
            circle at 86% 84%,
            rgba(243, 181, 98, 0.16),
            transparent 28%
        ),
        #101416;

    font-family: 'DM Sans', sans-serif;
}

.carousel {
    width: min(100%, 860px);
    padding: clamp(24px, 5vw, 54px);
    overflow: hidden;
    position: relative;

    border: 1px solid var(--line);
    border-radius: 18px;

    background: linear-gradient(
        145deg,
        rgba(31, 38, 42, 0.96),
        var(--panel)
    );

    box-shadow: 0 24px 80px rgba(0, 0, 0, 0.42);
}

.carousel::after {
    content: '';
    width: 180px;
    height: 180px;

    position: absolute;
    right: -80px;
    top: -90px;

    border: 1px solid rgba(243, 181, 98, 0.4);
    border-radius: 50%;

    box-shadow:
        0 0 0 24px rgba(243, 181, 98, 0.04),
        0 0 0 48px rgba(243, 181, 98, 0.025);

    pointer-events: none;
}

h1 {
    margin: 0 0 28px;

    color: var(--ink);

    font-family: 'Space Grotesk', sans-serif;
    font-size: clamp(2rem, 5vw, 3.8rem);
    line-height: 0.98;
    letter-spacing: -0.04em;
}

.image-container {
    width: 100%;
    aspect-ratio: 16 / 9;

    display: grid;
    place-items: center;

    overflow: hidden;

    border: 1px solid var(--line);
    border-radius: 12px;

    background:
        linear-gradient(
            135deg,
            rgba(243, 181, 98, 0.18),
            transparent 45%
        ),
        #252d30;
}

.image-container img {
    width: 100%;
    height: 100%;

    display: block;

    object-fit: cover;

    transition: transform 400ms ease;
}

.image-container:hover img {
    transform: scale(1.03);
}

.buttons {
    display: flex;
    justify-content: space-between;
    gap: 14px;

    margin-top: 22px;
}

button {
    min-width: 124px;

    padding: 13px 20px;

    border: 1px solid rgba(243, 181, 98, 0.68);
    border-radius: 999px;

    color: #211a14;
    background: var(--accent);

    font: 700 0.9rem 'DM Sans', sans-serif;

    cursor: pointer;

    transition:
        transform 180ms ease,
        background 180ms ease,
        box-shadow 180ms ease;
}

button:hover {
    background: #ffd08b;

    box-shadow: 0 8px 24px rgba(243, 181, 98, 0.22);

    transform: translateY(-2px);
}

button:active {
    transform: translateY(0);
}

button:focus-visible {
    outline: 3px solid var(--ink);
    outline-offset: 3px;
}

@media (max-width: 480px) {

    body {
        padding: 16px;
    }

    .carousel {
        padding: 24px 18px 20px;
    }

    .buttons {
        gap: 10px;
    }

    button {
        min-width: 0;
        flex: 1;
        padding-inline: 12px;
    }
}
```


## OUTPUT

<img width="1041" height="495" alt="image" src="https://github.com/user-attachments/assets/3c73e087-0cee-4eba-bcd1-d5a32089c5af" />

## RESULT
The program for creating Image Carousel using React is executed successfully.
