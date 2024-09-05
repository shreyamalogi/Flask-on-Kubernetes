
# Flask App on Kubernetes

Once upon a time, there was a simple web app that wanted to share the current time with the world. It didn’t need much—just a place to live, a way to run anywhere, and a team of helpers to make sure it was always available. So, the app’s creator gave it life using **Flask**, packed it up with **Docker**, and sent it to the magical land of **Kubernetes**.

## Chapter 1: The Birth of the App

In a quiet Python script, the web app was born. Its only purpose? To greet visitors with the time of their visit. Using **Flask**, it was given a voice—a simple API endpoint that whispered the time whenever anyone asked.


## Chapter 2: Packing for the Journey

The creator knew that the app couldn’t travel the world on its own. So, it was tucked into a **Docker** container, along with everything it needed—its Python runtime, dependencies, and code.

With this Dockerfile, the app could be packed into a suitcase, ready to be deployed anywhere.

## Chapter 3: The Land of Kubernetes

The creator sent the app to **Kubernetes**, a land where many copies of the app could be run at the same time. Kubernetes ensured that the app would always be available to visitors, no matter what happened to one of its copies.

The app was given a special Kubernetes **Deployment**, a set of instructions that told Kubernetes to create five copies of the app:


## Chapter 4: Making the App Easy to Find

To help visitors find the app, Kubernetes created a **Service**. This service acted as a phone number for the app. Anyone who called this number (or typed its address) would be directed to one of the app's copies.


## Chapter 5: The Adventure Begins

With everything set up, Kubernetes kept five copies of the app running, ensuring that it was always available. Visitors could type in the app’s address and see the current time, delivered straight from one of the five running copies. Even if one copy fell, Kubernetes would heal it, creating a new one in its place.

## Chapter 6: A New Life

And so, the Flask app lived a happy life in Kubernetes, scaling up or down as needed, always ready to greet its visitors with the time. Thanks to its creator's foresight and Kubernetes' magic, the app’s story continues, running smoothly day and night.

---

## Technical Walkthrough

### Prerequisites

To begin your own journey with this Flask app, make sure you have the following tools installed:

- **Docker**: To package the app into a container.
- **Kubernetes**: To deploy the app in a cluster (use Minikube for local setup or a cloud provider like GKE).
- **kubectl**: The command-line tool to interact with your Kubernetes cluster.

---

### Steps to Build and Deploy

#### 1. Build the Docker Image
First, clone the app’s repository and navigate to the project directory:

```bash
git clone <repository-url>
cd <repository-directory>
```

Create a `requirements.txt` file with Flask listed:

```bash
Flask==2.0.1
```

Now, build the Docker image:

```bash
docker build -t flask-kubernetes .
```

#### 2. Push the Image to a Registry
Log in to Docker Hub:

```bash
docker login
```

Tag and push the image:

```bash
docker tag flask-kubernetes <your-dockerhub-username>/flask-kubernetes
docker push <your-dockerhub-username>/flask-kubernetes
```

#### 3. Deploy the App to Kubernetes

Start your Kubernetes cluster (e.g., using Minikube):

```bash
minikube start
```

Apply the Kubernetes Deployment and Service configurations:

```bash
kubectl apply -f deployment.yaml
kubectl apply -f service.yaml
```

Verify that the app is running:

```bash
kubectl get deployments
```

#### 4. Access the App

- For Minikube users, simply run:

```bash
minikube service flask-test-service
```

- For cloud Kubernetes clusters, use the external IP of the LoadBalancer service:

```bash
http://<EXTERNAL-IP>:6000
```

You’ll see a JSON response with the current time of the call!

---

## The End

And so, the Flask app found a permanent home in Kubernetes, where it continues to live, grow, and serve the time to visitors all around the world.

The End.
