<script>
	/* 
  Starter code by Connor Rothschild https://twitter.com/CL_Rothschild
	Scrollytelling component from Russell Goldenberg https://twitter.com/codenberg/status/1432774653139984387 
  Where's waldo implementation by Schubert de Abreu https://twitter.com/schubertda1
  */
	
  import Scrolly from "../../shared/Scrolly.svelte";
  import Waldo from "./chart/Waldo.svelte";
	
  let value;
  const steps = [
		"<p>Early on the elite unit tasked with the job of finding elusive individual known as Waldo.</p>",
    "<p>Intel (not the company) said that he was in a compound at the bottom of the page.</p>",
    "<p>However a raid of the property turned up empty. The commander was certain though, that Waldo was surely nearby.</p>",
    "<p>The search perimeter was expanded as units were deployed to search nearby buildings. <br> They had no luck in the first building.</p>",
    "<p>On reaching the third house, the task force caught a break - a man wearing a red-and-white-striped shirt, bobble hat, round glasses and blue jeans told them that Waldo was not too far ahead.</p>",
    "<p>The search continues...</p>",
    ];
</script>
<section>
  <div class="section-container">
    <div class="steps-container">
      <Scrolly bind:value>
        {#each steps as text, i}
          <div class="step" class:active={value === i}>
            <div class="step-content">{@html text}</div>
          </div>
        {/each}
        <div class="spacer" />
      </Scrolly>
    </div>
    <div class="sticky">
      
      <Waldo step={value} ></Waldo>
      <!-- <Scatterplot step={value} /> -->
    </div>
  </div>
</section>

<style>
	:global(body) {
		overflow-x: hidden;
	}
	
  .spacer {
    height: 40vh;
  }

  .sticky {
    position: sticky;
    top: 5%;
		flex: 1 1 60%;
    width: 100%;
		margin: auto;
  }

  .section-container {
    margin-top: 0em;
    text-align: center;
    transition: background 100ms;
    display: flex;
      flex-direction: column-reverse;
  }

  .step {
    height: 80vh;
    display: flex;
    place-items: center;
    justify-content: center;
  }

  .step-content {
    font-size: 1rem;
    background: whitesmoke;
    color: #ccc;
    border-radius: 5px;
    padding: .5rem 1rem;
    display: flex;
    flex-direction: column;
    justify-content: center;
    transition: background 500ms ease;
    box-shadow: 1px 1px 10px rgba(0, 0, 0, .2);
    text-align: left;
		width: 70%;
		margin: auto;
		max-width: 500px;
  }

	.step.active .step-content {
		background: white;
		color: black;
	}
	
  .steps-container,
  .sticky {
    height: 100%;
  }

  .steps-container {
    flex: 1 1 40%;
    z-index: 10;
  }
</style>
