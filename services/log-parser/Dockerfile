FROM python:3.10.5-slim

ENV OS_ENV=linux

WORKDIR /app

RUN apt-get update \
    && apt-get install --no-install-recommends -y \
    build-essential
RUN pip install --no-cache-dir poetry==1.7.1

COPY pyproject.toml poetry.lock ./
RUN poetry config virtualenvs.create true && \
    poetry config virtualenvs.in-project true && \
    poetry install --no-root --no-dev --no-interaction

COPY . .

CMD ["poetry", "run", "python", "src/main.py"]