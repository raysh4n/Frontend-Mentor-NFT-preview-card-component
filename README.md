# Frontend Mentor - NFT preview card component solution

This is a solution to the [NFT preview card component challenge on Frontend Mentor](https://www.frontendmentor.io/challenges/nft-preview-card-component-SbdUL_w0U). Frontend Mentor challenges help you improve your coding skills by building realistic projects. 

## Table of contents

- [Overview](#overview)
  - [The challenge](#the-challenge)
  - [Screenshot](#screenshot)
  - [Links](#links)
- [My process](#my-process)
  - [Built with](#built-with)
  - [What I learned](#what-i-learned)
  - [Continued development](#continued-development)
  - [Useful resources](#useful-resources)
- [Author](#author)
- [Acknowledgments](#acknowledgments)

**Note: Delete this note and update the table of contents based on what sections you keep.**

## Overview

### The challenge

Users should be able to:

- View the optimal layout depending on their device's screen size
- See hover states for interactive elements

### Screenshot
Main
<br>
![](/Screenshot%202025-01-19%20213526.png)
<br>


Active State #1 
<br>
![](//active%20state%201.png)
<br>


Active State #2
<br>
![](/active%20state2.png)
<br>

Active State #3   
<br>
![](/active%20state%203.png)
<br>


### Links

- Solution URL: [here](https://www.frontendmentor.io/solutions/nft-preview-card-component-Q8KV5DA1AK)
- Live Site URL: [here](https://fem-nf-preview-card-component-raysh3n.netlify.app/)

## My process

### Built with

- Semantic HTML5 markup
- CSS custom properties
- Flexbox
- CSS Grid
- Mobile-first workflow

**Note: These are just examples. Delete this note and replace the list above with your own choices**

### What I learned

Use this section to recap over some of your major learnings while working through this project. Writing these out and providing code samples of areas you want to highlight is a great way to reinforce your own knowledge.

To see how you can add code snippets, see below:

```html
    <div class="card__background">
                <img class="card__view" src="/images/icon-view.svg" alt="view icon">
            </div>
```


To achive the hover effect for the background image
```css
.card__background {
    background-image: url("/images/image-equilibrium.jpg");
    background-repeat: no-repeat;
    background-size: cover;
    background-position: center;

    width: 100%;
    aspect-ratio: 1/1;
    border-radius: 8px;
    position: relative;
    transition: background-color 0.3s ease, background-blend-mode 0.3s ease;
}




.card__view {
    width: 3rem;
    position: absolute; /*using absolute in relative to the background for the view icon to be centered via top, left and translate*/
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%); /*after the top left position, move 50% to left and 50% to up from the position*/
    /* display: none; */
opacity: 0;
transition: opacity 0.3s ease; /* Smooth transition */
}



card__background:hover {
    cursor: pointer;
    background-image: url("/images/image-equilibrium.jpg");
    background-color: var(--clr-cyan);
    background-repeat: no-repeat;
    background-size: cover;
    background-position: center;
    background-blend-mode: multiply; /*using blend more to achieve the desdired color effect*/
}

.card__background:hover .card__view { /*this selector allows when hovered only display the view icon, display:block will not work for transition so used opacity*/
    /* display: block; */
    opacity: 1;
}
```


To achieve the proper hover effect usese ::before , scrap the top left translate, uses z-index
```css

.card__background {
	background-image: url("/images/image-equilibrium.jpg");
	background-repeat: no-repeat;
	background-size: cover;
	background-position: center;

	width: 100%;
	aspect-ratio: 1/1;
	border-radius: 8px;
	position: relative; /*for overlay through ::before*/
display: flex;
	justify-content: center;
	align-items: center;
	transition: background-color 0.3s ease /*, background-blend-mode 0.3s ease*/;
}




.card__view {
	width: 3rem;
	/* position: absolute;
	top: 50%;
	left: 50%;
	transform: translate(-50%, -50%); */
	/* display: none; */
opacity: 0;
transition: opacity 0.3s ease; /* Smooth transition */
z-index: 1;
}






.card__background::before {
	content:"";
	position:absolute;
width: 100%;
	aspect-ratio: 1/1;
	border-radius: inherit;
	background-color: var(--clr-cyan5);
	opacity: 0;
	transition:opacity 0.3s ease

}



 /* .card__background:hover {
	cursor: pointer;
	background-image: url("/images/image-equilibrium.jpg");
	background-color: var(--clr-cyan5);
	background-repeat: no-repeat;
	background-size: cover;
	background-position: center;
	background-blend-mode:multiply;
}  */


.card__background:hover::before { /*notice this selector how it's being used*/
	cursor: pointer;
	opacity: 1;
}

.card__background:hover .card__view {
	/* display: block; */
	opacity: 1;
}
```

Some other implementation of selector. Using nth-child()
```css
.card__info div:nth-child(1) { /*using nth-child() selector*/
}

```





