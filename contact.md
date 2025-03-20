---
layout: page
permalink: /contact/
---

<div class="contact-container">
    <div class="contact-info">
        <h2>Get In Touch</h2>
        <p>Ready to transform your waste management business with AI-powered solutions? Our team is here to help.</p>
        
        <div class="contact-methods">
            <div class="contact-method">
                <div class="contact-icon">📧</div>
                <h3>Email</h3>
                <p><a href="mailto:wasteiqai@gmail.com">wasteiqai@gmail.com</a></p>
            </div>
            
            <div class="contact-method">
                <div class="contact-icon">📱</div>
                <h3>Phone</h3>
                <p><a href="tel:+35312345678">+35312345678</a></p>
            </div>
        </div>
    </div>
    
    <div class="contact-form-container">
        <h2>Request a Demo</h2>
        <form class="contact-form" id="demo-request-form" action="https://formspree.io/f/mrbpeojq" method="POST">
            <div class="form-group">
                <label for="name">Name</label>
                <input type="text" id="name" name="name" required>
            </div>
            
            <div class="form-group">
                <label for="company">Company</label>
                <input type="text" id="company" name="company" required>
            </div>
            
            <div class="form-group">
                <label for="email">Email</label>
                <input type="email" id="email" name="email" required>
            </div>
            
            <div class="form-group">
                <label for="phone">Phone</label>
                <input type="tel" id="phone" name="phone">
            </div>
            
            <div class="form-group">
                <label for="message">Message</label>
                <textarea id="message" name="message" rows="4"></textarea>
            </div>
            
            <div class="form-group">
                <label for="solution">I'm interested in:</label>
                <select id="solution" name="solution">
                    <option value="both">Both Solutions</option>
                    <option value="salesiq">SalesIQ</option>
                    <option value="retentioniq">RetentionIQ</option>
                </select>
            </div>
            
            <input type="text" name="_gotcha" style="display:none">
            
            <button type="submit" class="submit-button">Request Demo</button>
            <p id="my-form-status"></p>
        </form>
    </div>
</div>

<script>
  var form = document.getElementById("demo-request-form");
  
  async function handleSubmit(event) {
    event.preventDefault();
    var status = document.getElementById("my-form-status");
    var data = new FormData(event.target);
    fetch(event.target.action, {
      method: form.method,
      body: data,
      headers: {
          'Accept': 'application/json'
      }
    }).then(response => {
      if (response.ok) {
        status.innerHTML = "Thank you for your submission! We will be in contact shorty.";
        status.className = 'success';
        form.reset()
      } else {
        response.json().then(data => {
            status.className = 'error';
          if (Object.hasOwn(data, 'errors')) {
            status.innerHTML = data["errors"].map(error => error["message"]).join(", ")
          } else {
            status.innerHTML = "Oops! There was a problem submitting your form"
          }
        })
      }
    }).catch(error => {
      status.innerHTML = "Oops! There was a problem submitting your form"
    });
  }
  form.addEventListener("submit", handleSubmit)
</script> 