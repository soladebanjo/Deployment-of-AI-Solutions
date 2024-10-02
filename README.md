# Deployment of AI Solutions

## Overview

Here's a project that shows off a basic machine learning app, put together Flask & Docker. It uses something called a Tree Classifier to guess what kind of iris flower you've got, just by looking at its sepal & petal sizes. The model gets its smarts from the well-known Iris dataset. You'll find a nifty /predict endpoint in the Flask app that handles all your guesses.

## Project Structure

The project has these files:

* **Dockerfile**: Here, you'll find steps to whip up the Docker image for the app.
* **requirements.txt**: This lists all the Python packages you need for running everything smoothly.
* **train\_model.py**: A script for training that Decision Tree model with the Iris dataset.
* **app.py**: This is where the Flask app lives, taking care of predictions via an API.
* **model.pkl**: The trained model is stashed here, saved for future guesses.

## Instructions to Build & Run the Docker Container

Follow these steps to get everything running inside Docker:

1. **Clone the repository:**

    ```bash
    git clone https://github.com/soladebanjo/Deployment-of-AI-Solutions.git
    cd Deployment-of-AI-Solutions
    ```
2. **Build the Docker image:** Use this command to put together that Docker image:

    ```bash
    sudo docker build -t ml-app .
    ```
3. **Run the Docker container:** Fire up that container & link port 4000 of it to port 80 on your system:

    ```bash
    sudo docker run -p 4000:80 ml-app
    ```
4. **Access the Application:** Pop open your browser & head on over to this link:

    ```
    http://localhost:4000
    ```

    If it's all set up on a remote server, switch out "localhost" with your server's IP address, like this:

    ```
    http://<your-server-ip>:4000
    ```

## Testing the ML Endpoint

You can give that /predict endpoint a spin with curl or Postman by hitting it with a POST request packed with JSON data.

**Example using curl:**

```bash
curl -X POST http://localhost:4000/predict -H "Content-Type: application/json" -d '{"input": [5.1, 3.5, 1.4, 0.2]}'
```

You'll get back something like this:

```json
{
  "prediction": 0
}
```

In this case, class 0 could mean one of those Iris species—like Iris-setosa or even Iris-versicolor.

**Example using Postman:**

* Set your go-to method as POST.
* Tap in this URL: http://localhost:4000/predict
* Over in Body tab, pick raw & set format to JSON.
* Enter this JSON data:

    ```json
    {
      "input": [5.1, 3.5, 1.4, 02]
    }
    
    ```
* Hit send and you'll get back a JSON response showing off that prediction.

## Technologies Used

* Python 3.9
* Flask for running the API.
* Scikit-learn to build our machine-learning model.
* Docker for containerizing everything so it works anywhere you want it.

## Acknowledgements

This project smartly uses the Scikit-learn library's Iris dataset—it’s famous mind you—for training itself. The dataset’s great for playing around with machine learning & data analysis; popular with folks who do classification tasks often.

## License

The MIT License covers this whole project! More details? Check out the LICENSE file.
